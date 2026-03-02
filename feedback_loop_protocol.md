# Feedback Loop Protocol
## Quy Trình Cập Nhật Formulas Từ Performance Data

**VERSION**: 1.0  
**CREATED**: 05/02/2026  
**OWNER**: Content Strategy Team

---

## MỤC ĐÍCH

File này định nghĩa quy trình **closed-loop** để:
1. Thu thập performance data
2. Phân tích patterns (winner/loser)
3. Update formulas dựa trên data
4. Track version changes

**Nguyên tắc core:** Data drives decisions, không phải cảm tính.

---

## PHẦN 1: PERFORMANCE CLASSIFICATION

### 1.1. Hook Performance Tiers

| Tier | 3s Retention | Classification | Action |
|------|--------------|----------------|--------|
| **WINNER** | ≥70% | Replicate pattern | Document → Scale → Add to examples |
| **GOOD** | 55-69% | Keep using | Document pattern, minor optimize |
| **TEST** | 40-54% | Needs iteration | Test variations, don't abandon |
| **LOSER** | <40% | Rebuild | Post-mortem → Identify failure → Don't reuse |

### 1.2. Script Performance Tiers

| Tier | Completion Rate | Classification | Action |
|------|-----------------|----------------|--------|
| **WINNER** | ≥50% | Strong structure | Document → Replicate |
| **GOOD** | 35-49% | Acceptable | Keep, optimize transitions |
| **TEST** | 25-34% | Needs work | Identify drop-off points |
| **LOSER** | <25% | Failed | Post-mortem → Major revision |

### 1.3. Ghi Nhận Classification

Sau mỗi video (48-72h post-publish), ghi nhận:

```
Video ID: [TK_YYYYMMDD_XXX]
Date: [ngày đăng]
Hook Formula: [CG-001 / PI-001 / etc.]
Script Formula: [SF-001 / SF-008 / etc.]
3s Retention: [XX%]
Completion Rate: [XX%]
Classification: [WINNER / GOOD / TEST / LOSER]
Notes: [Observation ngắn]
```

---

## PHẦN 2: TRIGGERS ĐỂ UPDATE FORMULAS

### 2.1. Khi nào UPDATE formula?

| Trigger | Condition | Action |
|---------|-----------|--------|
| **Consistent Winner** | Formula có 3+ WINNER liên tiếp | Promote to "Proven", tăng priority |
| **Consistent Loser** | Formula có 3+ LOSER liên tiếp | Revise hoặc Retire |
| **Pattern Discovery** | Thấy pattern mới từ winner video | Extract → Create new formula |
| **Variable Insight** | Phát hiện variable range tốt/xấu | Update variable constraints |
| **Audience Shift** | Metrics thay đổi đột ngột (>20%) | Review tất cả formulas |

### 2.2. Khi nào KHÔNG update?

- Chỉ có 1-2 data points (chưa đủ sample)
- External factors ảnh hưởng (algorithm change, trend, thời điểm đăng)
- Performance chênh lệch <10% so với baseline

---

## PHẦN 3: UPDATE WORKFLOW

### Step 1: Thu Thập Data (Weekly)

**Thứ 2 hàng tuần:**
1. Mở Looker Studio
2. Filter videos từ tuần trước
3. Ghi nhận metrics cho từng video
4. Classify mỗi video (WINNER/GOOD/TEST/LOSER)

**Output:** List videos + classification

---

### Step 2: Pattern Analysis (Weekly)

**Câu hỏi cần trả lời:**

**Cho Winners:**
- Hook formula nào perform tốt nhất?
- Script formula nào perform tốt nhất?
- Có common elements gì? (topic type, timing, emotion)
- Variables nào được dùng? (percentage range, emotion type)

**Cho Losers:**
- Failure point ở đâu? (Hook? Transition? Body? Product intro?)
- Formula nào consistently fail?
- Có pattern gì chung? (quá dài, quá aggressive, wrong emotion)

**Output:** Insights document (bullet points)

---

### Step 3: Decision Making (Weekly)

Dựa trên analysis, quyết định:

| Insight | Decision | Priority |
|---------|----------|----------|
| Formula X có 4/5 WINNER | Promote, add more examples | High |
| Formula Y có 3/5 LOSER | Revise variables hoặc retire | High |
| Phát hiện pattern mới | Create new formula entry | Medium |
| Variable range insight | Update constraints | Medium |
| Minor optimization idea | Note for future | Low |

**Output:** Action items list

---

### Step 4: Execute Updates (Weekly/Bi-weekly)

**Cho Hook Formulas (hook_formulas.json):**

```json
// Khi update, thêm vào version_history:
{
  "id": "CG-001",
  "current_version": "1.2",
  
  "version_history": [
    {
      "version": "1.2",
      "date": "2026-02-05",
      "trigger": "3/5 tests với percentage >85% failed credibility",
      "changes": "Giảm percentage range từ 60-90 xuống 65-80",
      "evidence": "Video TK_0201, TK_0203, TK_0205 có 3s retention <35% với số 87%, 92%"
    }
  ],
  
  "variables": {
    "percentage": {
      "range": "65-80",  // UPDATED
      "note": "Đã test, 65-80 credible nhất. >85% triggers BS detector."
    }
  },
  
  "success_rate": "68%",  // UPDATED từ data
  "total_tests": 15       // UPDATED
}
```

**Cho Script Formulas (script_formulas.json):**

```json
{
  "id": "SF-008",
  "current_version": "1.1",
  
  "version_history": [
    {
      "version": "1.1", 
      "date": "2026-02-05",
      "trigger": "Retention drop >30% at 70s mark consistently",
      "changes": "Added note: 4 chunks risky, recommend compress to 3 for most topics",
      "evidence": "Video TK_0128, TK_0130 had cliff drop at chunk 4"
    }
  ],
  
  "constraints": [
    "4 chunks = High risk. CHỈ dùng khi topic THỰC SỰ cần. Prefer 3 chunks.",  // UPDATED
    // ... other constraints
  ],
  
  "success_rate": "45%",
  "total_tests": 8
}
```

**Cho Examples (Hook-Examples.md hoặc trong formula):**

Thêm winner/loser cases với full context:

```markdown
## WINNER CASE #X

**Video ID:** TK_20260201_001
**Hook:** "72% nam giới sau 30 testosterone giảm - Bạn có biết nguyên nhân thật sự?"
**Formula:** CG-001 v1.2

**Performance:**
- 3s Retention: 74%
- Completion: 52%
- Views: 85,000

**Why It Worked:**
- Percentage 72% trong sweet spot (65-80)
- "Nguyên nhân thật sự" tạo strong curiosity gap
- Topic match với audience pain point

**Pattern to Replicate:**
- Percentage + "nguyên nhân thật sự" combo
- Keep percentage ≤80%
```

---

### Step 5: Communicate Changes (Weekly)

Sau khi update, notify team:

```
📢 FORMULA UPDATE - Week of [Date]

**Changes Made:**
1. CG-001: Percentage range 60-90 → 65-80 (credibility issue)
2. SF-008: Added warning về 4 chunks retention risk
3. NEW: Added Winner example TK_0201 to CG-001

**Key Insights:**
- Percentage >85% consistently fails (BS detector)
- 4-chunk scripts có cliff drop after 60s

**Next Week Focus:**
- Test CG-002 với emotional topics
- Monitor SF-008 với 3-chunk version
```

---

## PHẦN 4: FORMULA LIFECYCLE

### 4.1. Formula States

```
[NEW] → [TESTING] → [PROVEN] → [OPTIMIZING] → [RETIRED]
         ↑                                        |
         └────────────────────────────────────────┘
                    (Revival nếu có new insight)
```

| State | Criteria | Action |
|-------|----------|--------|
| **NEW** | Vừa tạo, 0 tests | Test với 3-5 videos |
| **TESTING** | 1-5 tests, chưa đủ data | Continue testing, collect data |
| **PROVEN** | 5+ tests, success_rate ≥60% | Scale usage, document patterns |
| **OPTIMIZING** | Proven but có room improve | A/B test variations |
| **RETIRED** | Success_rate <40% sau 10+ tests | Stop using, archive |

### 4.2. Khi nào Retire Formula?

- Success rate <40% sau 10+ tests
- Audience/platform shift làm formula obsolete
- Có formula mới tốt hơn replace hoàn toàn

**Retire Process:**
1. Move formula to `retired_formulas` section (không xóa)
2. Note reason for retirement
3. Keep for reference (có thể revival sau)

---

## PHẦN 5: MONTHLY REVIEW

**Vào ngày 1 mỗi tháng:**

### 5.1. Metrics Summary

| Formula | Tests | Success Rate | Trend | Status |
|---------|-------|--------------|-------|--------|
| CG-001 | 15 | 68% | ↑ +5% | Proven |
| CG-002 | 8 | 52% | → Stable | Testing |
| SF-008 | 8 | 45% | ↓ -10% | Review needed |

### 5.2. Questions to Answer

1. Formula nào perform best tháng này?
2. Formula nào cần attention/revision?
3. Có new patterns discovered?
4. Audience behavior có shift không?
5. Có formula nào nên retire?

### 5.3. Action Plan for Next Month

- [ ] Focus test: [formula cần more data]
- [ ] Optimize: [formula cần improve]
- [ ] Create: [new formula ideas]
- [ ] Retire: [formula không còn work]

---

## PHẦN 6: TOOLS & TEMPLATES

### 6.1. Weekly Tracking Template

```markdown
# WEEKLY PERFORMANCE LOG - Week of [Date]

## Videos Published
| Video ID | Hook | Script | 3s Ret | Completion | Class |
|----------|------|--------|--------|------------|-------|
| TK_0201 | CG-001 | SF-001 | 68% | 45% | GOOD |
| TK_0203 | PI-001 | SF-008 | 42% | 28% | TEST |

## Winners This Week
- [Video ID]: [What worked]

## Losers This Week  
- [Video ID]: [What failed]

## Insights
- [Bullet points]

## Action Items
- [ ] [Action 1]
- [ ] [Action 2]
```

### 6.2. Formula Update Checklist

Khi update formula, ensure:
- [ ] Updated `current_version` number
- [ ] Added entry to `version_history` với date, trigger, changes, evidence
- [ ] Updated `success_rate` và `total_tests`
- [ ] Updated relevant `variables` constraints nếu có
- [ ] Updated `constraints` section nếu có new learnings
- [ ] Added new examples nếu có winner/loser cases
- [ ] Notified team về changes

---

## APPENDIX: VERSION NUMBERING

**Format:** `Major.Minor`

- **Major** (1.0 → 2.0): Structural change (new phase, different flow)
- **Minor** (1.0 → 1.1): Variable tweak, constraint update, example addition

**Examples:**
- 1.0 → 1.1: Thay đổi percentage range
- 1.1 → 1.2: Thêm new winner example
- 1.2 → 2.0: Restructure từ 4 chunks xuống 3 chunks

---

**END OF DOCUMENT**