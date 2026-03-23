# program.md — TikTok Content Auto-Research System
**VERSION**: 1.0 | **Last Updated**: 2026-03-23
**Inspired by**: Karpathy's autoresearch (github.com/karpathy/autoresearch)

---

## 🎯 WHAT THIS SYSTEM IS

This is an **automatically self-improving content pipeline** for a Vietnamese men's health TikTok channel (InnOut brand, persona: Professor Simon).

The system applies Karpathy's autoresearch loop principle to content creation:
- **`train.py`** equivalent → `hook_formulas.json` + `script_formulas.json` (the files the agent modifies)
- **`program.md`** equivalent → This file (instructions for the agent)
- **Eval metric** → Real TikTok performance data: HHR (3s retention), VMI (virality), ERS (engagement), HSP (hook score)

**The core loop (runs every 24 hours):**
```
Publish video → Collect real metrics (72h) → Score with eval → 
Correlate eval score vs actual views → Identify winners/failures → 
Rewrite hook_formulas.json → Push to GitHub → Next generation uses improved formulas
```

---

## 🏗️ SYSTEM ARCHITECTURE (6 n8n Workflows)

### WF-001: Script Generation Pipeline
**Trigger**: Slack slash command `/generate [topic] | [pain_point] | [yes/no] | [product_name]`

**Flow**:
1. Parse input from Slack
2. Validate topic + pain_point are present
3. Immediately respond to Slack (⏳ message) to avoid 3s timeout
4. Load 7 Knowledge Base files from GitHub (in parallel):
   - `context.md`, `persona.md`, `psychology_of_content_instruction_guide.md`
   - `hook_formulas.json`, `script_formulas.json`, `output-format.md`, `MASTER_INDEX.md`
5. Check Google Sheets (`ContentPipeline_VideoTracker`) for last 3 hook formulas used (rotation rule)
6. Build system prompt with full KB context
7. Call Claude API (`claude-sonnet-4-5`) → generates 3 hook+script options
8. Send options to Slack as interactive buttons (Select A / Select B / Select C / Regenerate)
9. Log request to Google Sheets (status: DRAFT)

**Key rules**:
- Never reuse hook formula from last 3 videos (rotation rule)
- Output must be valid JSON with 3 options, each containing full_script object
- Vietnamese language only for script content

---

### WF-002: Approval Handler
**Trigger**: Slack button click (from WF-001 output)

**Flow**:
1. Receive Slack interaction payload
2. Parse: which option selected, by whom
3. Build production brief (full script formatted as markdown)
4. Update Google Sheets: status → IN_PRODUCTION, log selected formula
5. Notify `#production-board` channel with brief
6. Reply in original Slack thread: "✅ Option X selected by [user]"

---

### WF-003: Post-Publish Logger
**Trigger**: Slack slash command `/published [tiktok_url]`

**Flow**:
1. Parse TikTok URL → extract video_id
2. Find the most recent IN_PRODUCTION row in Google Sheets
3. Update row: video_id, tiktok_url, published_at, status → PUBLISHED
4. Respond: "✅ Video logged. Auto-analysis scheduled for 72h."

---

### WF-004: Analysis Pipeline (THE EVAL ENGINE)
**Trigger**: Cron — every day at 09:00 Asia/Ho_Chi_Minh

**Flow**:
1. Read all rows from `ContentPipeline_VideoTracker`
2. Filter: status = PUBLISHED AND published_at > 72 hours ago
3. For each video: request metrics via Slack (`#content-pipeline`)
4. Wait for team to submit metrics via `/metrics-input` command
5. Calculate advanced metrics:
   - **HHR** = retention_3s / 100 (Hook Hold Rate — primary metric)
   - **ERS** = (likes + comments×2 + shares×3) / views (Engagement Rate Score)
   - **VMI** = (for_you_pct/100) × (shares/views) × (retention_3s/100) × 100 (Virality Momentum Index)
   - **CAHE** = (new_viewer_pct × retention_3s) / for_you_pct (Cold Audience Hook Effectiveness)
   - **ADR** = avg drop rate between 3s→7s and 7s→15s (Audience Drop Rate)
   - **HBAS** = (retention_3s/100) × (retention_15s/retention_3s) (Hook-to-Body Attention Score)
   - **HSP** = composite score (0.35×HHR + 0.20×retention + 0.25×ERS + 0.10×FYP + 0.10×new) (Hook Success Probability)
6. Classify video: WINNER (HHR≥0.70 AND VMI≥2.0) | GOOD (HHR≥0.55) | MINIMUM (HHR≥0.40) | FAILED
7. Log all metrics to `ContentPipeline_MetricsData` sheet
8. Call Claude Analysis Agent with full context (metrics_evaluation.md + Hook-Examples.md + current formulas + last 5 decisions)
9. Claude outputs: classification, key_insights[], recommendations[] (each with type, target_file, target_id, field, old_value, new_value, reasoning, confidence)
10. Send Slack report with Approve/Reject buttons per recommendation
11. Update video tracker: classification, analysis_date, status → ANALYZED

---

### WF-005: Knowledge Base Updater (THE SELF-IMPROVEMENT ENGINE)
**Trigger**: Slack button click (Approve/Reject from WF-004 reports)

**Flow (Approve path)**:
1. Parse recommendation payload
2. Snapshot current file content from GitHub (for rollback)
3. Apply change to target file:
   - `update_stats`: Update success_rate, avg_performance fields in hook_formulas.json
   - `add_case_study`: Append new example to Hook-Examples.md
   - `modify_formula`: Change formula structure, variables, or weight
4. Commit & push to GitHub with structured commit message: `[AUTO] D-{id}: {type} - {reasoning}`
5. Log to `ContentPipeline_DecisionLog`: decision_id, timestamp, recommendation, decision, applied_to_file, rollback_snapshot, github_commit_sha
6. Notify Slack: "✅ KB updated. Changes active in next generation."

**Flow (Reject path)**:
1. Log rejection to DecisionLog with rejection_reason
2. Notify Slack: "❌ Recommendation rejected. Logged for future analysis."

---

### WF-006: Weekly Digest
**Trigger**: Cron — every Monday at 08:00 Asia/Ho_Chi_Minh

**Flow**:
1. Read last 7 days from VideoTracker, MetricsData, DecisionLog
2. Calculate: videos published, classification breakdown, top/worst formula, approval rate
3. Send formatted summary to `#content-pipeline` Slack channel

---

## 📊 DATA STORES

### Google Sheets (ID: 146mZfHjUiYp3B5EP-Lop9_mkeSr1fC5G3fSXglpN45o)

**Sheet 1: ContentPipeline_VideoTracker**
Tracks every video from creation to analysis.
Key columns: `request_id`, `topic`, `pain_point`, `hook_formula_id`, `script_formula_id`, `dopamine_technique`, `selected_option`, `video_id`, `tiktok_url`, `published_at`, `status`, `classification`, `analysis_date`

Status flow: `DRAFT` → `IN_PRODUCTION` → `PUBLISHED` → `ANALYZED`

**Sheet 2: ContentPipeline_MetricsData**
Raw and calculated metrics per video per measurement.
Key columns: `video_id`, `measured_at`, views, retentions, HHR, ERS, VMI, CAHE, ADR, HBAS, HSP

**Sheet 3: ContentPipeline_DecisionLog**
Every approve/reject decision with full context + rollback capability.
Key columns: `decision_id`, `recommendation_type`, `decision`, `decision_by`, `applied_to_file`, `rollback_snapshot`, `github_commit`

---

## 🧠 KNOWLEDGE BASE FILES (GitHub: longnguyen911488/tiktok-knowledge-base)

| File | Role | Modified by system? |
|------|------|---------------------|
| `program.md` | This file — system overview | ❌ Human only |
| `MASTER_INDEX.md` | Navigation map for KB files | ❌ Human only |
| `context.md` | Audience profile, pain points, demographics | ❌ Human only |
| `persona.md` | Professor Simon voice, tone, xưng hô rules | ❌ Human only |
| `psychology_of_content_instruction_guide.md` | 8 psychology principles | ❌ Human only |
| `hook_formulas.json` | Hook templates with success_rate, avg_performance | ✅ **AUTO-UPDATED by WF-005** |
| `script_formulas.json` | Script body templates | ✅ **AUTO-UPDATED by WF-005** |
| `output-format.md` | Required 13-subsection output structure | ❌ Human only |
| `Hook-Examples.md` | Success/fail case studies with metrics | ✅ **AUTO-UPDATED by WF-005** |
| `metrics_evaluation.md` | 15+ metric formulas and thresholds | ❌ Human only |

**The files marked ✅ are the `train.py` equivalents** — they evolve automatically based on real performance data.

---

## 🔄 THE AUTO-RESEARCH LOOP IN DETAIL

```
Day 0: /generate topic | pain_point → Claude picks formula → Video produced
Day 1-3: Video published → Metrics accumulate
Day 3+: WF-004 runs → Metrics collected → Video scored
         Claude Analysis Agent evaluates:
           - Did HHR meet threshold? (≥0.55 = GOOD)
           - Did this hook formula outperform its historical average?
           - What correlation between eval criteria and actual performance?
         Agent recommends: "Update CG-001 success_rate from 0.73 to 0.81"
Day 4: Human reviews recommendation in Slack → Approve
         WF-005 auto-commits to GitHub → hook_formulas.json updated
Day 5+: WF-001 loads updated hook_formulas.json → Better formula selection
         Loop continues forever, compounding improvements
```

**The research log (DecisionLog sheet) is the most valuable asset.**
Every change is traceable: what changed, why, based on what data, who approved.
When a new Claude model is released, hand it the DecisionLog and it continues exactly where it left off.

---

## 📏 EVAL CRITERIA (Binary Yes/No — Machine Readable)

When analyzing a script's quality BEFORE publishing (predict performance):
1. Does the hook describe a RESULT or TRANSFORMATION? (not just a feature)
2. Does the hook address a SPECIFIC pain point from context.md?
3. Would a viewer understand the value proposition in first 3 seconds?
4. Does the script avoid sounding like an advertisement or product announcement?
5. Is there at least 1 specific number or piece of evidence in the body?
6. Is the hook under 10 seconds?
7. Does the outro include Professor Simon's catchphrase?
8. Is the language natural and conversational (not written-essay style)?
9. Does the script avoid vague phrases like "hiệu quả", "tốt cho sức khoẻ"?
10. Would the visual direction for the first frame stop someone from scrolling?

**Score**: Count YES answers → /10
- 8-10: High confidence, add to creation queue
- 5-7: Needs revision
- 0-4: Reject, regenerate

**Correlation tracking**: After publish, compare eval score vs actual HHR.
- High eval + High HHR = VALIDATED WINNER (formula works, eval criteria confirmed)
- High eval + Low HHR = FALSE POSITIVE (eval criteria needs refinement)
- Low eval + High HHR = ANOMALY (investigate, may reveal unknown pattern)

---

## 🔑 CREDENTIALS & INFRASTRUCTURE

| Service | Used by | Purpose |
|---------|---------|---------|
| Slack (Bot Token xoxb-...) | WF-001,002,003,004,005,006 | Commands + notifications |
| Google Sheets OAuth2 | WF-001,003,004,005,006 | Data storage |
| Claude API (Anthropic) | WF-001, WF-004 | Script generation + analysis |
| GitHub Token | WF-005 | Push KB file updates |
| n8n (Docker, port 5678) | All | Workflow orchestration |
| localtunnel / cloudflared | All | Expose n8n to Slack webhooks |

**Slack channels**:
- `#content-pipeline`: Main workspace (commands + script options)
- `#production-board`: Editor pickup + production briefs
- `#pipeline-logs`: Error notifications + system alerts

---

## ⚠️ KNOWN LIMITATIONS (Current Phase)

1. **TikTok metrics are manual** — Team submits raw numbers via Slack command. Phase 2 will automate via TikTok API.
2. **Tunnel URL changes on restart** — Every `npx n8n start` with localtunnel gives a new URL. Slack slash command URL must be updated manually.
3. **Knowledge base is Vietnamese-specific** — Context, persona, and all examples are for Vietnamese men's health content. Do not apply generic content logic.
4. **Google Sheets `script_formulas.json` column** — Currently stores formula ID only. Full formula content always fetched from GitHub.

---

## 🚀 QUICK REFERENCE FOR CLAUDE

**If you are the Script Generation Agent (WF-001)**:
- Your job: Generate 3 diverse hook+script options
- Constraints: No formula reuse (check recent 3), Vietnamese only, follow output-format.md
- Output: Valid JSON with options array

**If you are the Analysis Agent (WF-004)**:
- Your job: Analyze one video's performance, classify it, recommend KB updates
- Constraints: Only recommend changes to hook_formulas.json, script_formulas.json, or Hook-Examples.md
- Output: Valid JSON with classification, key_insights[], recommendations[]

**If you are reviewing the system**:
- The DecisionLog is your memory of what has been tried
- hook_formulas.json success_rate fields reflect real performance history
- Always check what changed recently before making new recommendations
