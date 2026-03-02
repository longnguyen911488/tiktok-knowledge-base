
# MASTER INDEX - Content Generation System
**VERSION**: 2.0 | **Last Updated**: 23/01/2026


## ⚠️ CRITICAL INSTRUCTION FOR AI
This file is your NAVIGATION MAP. You MUST reference all files listed below in the correct order for each task type.

---
## FORMULA vs STRUCTURE PRIORITY

When generating scripts:

**Priority Order**:
1. If using formula from script_formulas.json → Follow formula timing
2. If creating new script → Use script_structure.md as baseline
3. Structure guidelines are FLEXIBLE (±5s per phase OK)

**Principle**: Formulas = tested patterns (trust them). Structure = guidelines (adapt as needed).
---

## AI FORMULA SELECTION RULES

Khi chọn formula, AI phải tuân thủ:

### Hook Formula Selection:
1. **Rotation Rule**: KHÔNG dùng lại formula đã dùng trong 3 videos gần nhất (nếu có history)
2. **Technique Match**: 
   - Topic có số liệu mạnh → Ưu tiên CG-001 (Percentage Shock)
   - Topic sensitive (ED, PE, tâm lý) → Ưu tiên EM-001 (Emotional Mirroring) hoặc STORY-001
   - Topic cần debunk myth → Ưu tiên CG-002 (Wrong Belief Contradiction)
   - Topic urgency/warning → Ưu tiên PI-001 (Urgent Command)
3. **Random trong options phù hợp**: Nếu nhiều formula đều fit → Random chọn

### Script Formula Selection:
1. **Product_Include = True** → Chọn formula có product intro phase
2. **Product_Include = False** → Chọn formula educational pure
3. **Topic complexity**:
   - Simple topic → 3 chunks, 60s max
   - Complex topic → 4 chunks, 90-120s OK
4. **Audience mood**:
   - Cần empathy → SF với emotional arc
   - Cần authority → SF với scientific structure

### Output Requirement:
AI phải declare trong output:
## SYSTEM ARCHITECTURE

### A. FOUNDATION FILES (Always Load First)
**Purpose**: Context + Audience + Brand Voice
**When**: Every single content generation task

| File | Purpose | Key Sections | Must Read? |
|------|---------|--------------|-----------|
| `context.md` | Audience, pain points, desires | Pain Points, Desires, Demographics | ✅ MANDATORY |
| `persona.md` | Professor Simon voice/tone | Xưng hô, Tone, Catchphrase | ✅ MANDATORY |
| `psychology_of_content_instruction_guide.md` | Content psychology principles | 8 Principles | ✅ MANDATORY |

**Validation Question for AI**: 
- [ ] Can you name 3 pain points from context.md?
- [ ] What is Professor Simon's catchphrase?
- [ ] What are the Four Horsemen?

---

### B. HOOK GENERATION FILES
**Purpose**: Create 0-10s hook only
**When**: Task = "Generate hook" OR "Generate hook + script"

| File | Purpose | Must Read Sections | Must Read? |
|------|---------|---------------------|-----------|
| `hook_principle.md` | 8 dopamine techniques theory | All 8 techniques | ✅ MANDATORY |
| `Instruction.md` | Hook creation process | Section 9: Hook vs Body Separation | ✅ MANDATORY |
| `hook_formulas.json` | Proven hook templates | All formulas + examples | ✅ MANDATORY |
| `Hook-Examples.md` | Success/fail case studies | Success cases + Fail cases | ⚠️ REFERENCE |
| `visual-instruction.md` | Visual selection for hook | Category A, B, D | ⚠️ REFERENCE |
| `metrics_evaluation.md` | Hook performance metrics | Section on 3s retention | 📊 POST-PUBLISH |
| `output-format.md` | Output structure requirements | All | ✅ MANDATORY |

**Validation Checklist for AI**:
- [ ] Hook uses 1+ dopamine technique from hook_principle.md?
- [ ] Hook follows formula structure from hook_formulas.json?
- [ ] Hook does NOT reveal product name (per Instruction.md Section 9)?
- [ ] Output follows 13-subsection format from output-format.md?

---

### C. SCRIPT GENERATION FILES
**Purpose**: Create 10-60s body/script
**When**: Task = "Generate script" OR "Generate hook + script"

| File | Purpose | Must Read Sections | Must Read? |
|------|---------|---------------------|-----------|
| `script_formulas.json` | Body templates (transition, education, product intro, CTA) | All | ✅ MANDATORY |
| `script_examples.md` | Success/fail full scripts | Top 10 winners | ⚠️ REFERENCE |


**Validation Checklist for AI**:
- [ ] Transition from hook (10-15s) follows transition_techniques.md?
- [ ] Product name appears at 45-55s only (per script_structure.md)?
- [ ] Body structure matches formulas from script_formulas.json?
- [ ] Script applies psychology principles from psychology guide?

---

### D. VISUAL PRODUCTION FILES
**Purpose**: Visual direction for editor
**When**: After script is approved, need visual brief

| File | Purpose | Must Read? |
|------|---------|-----------|
| `visual-instruction.md` | Visual selection framework | ⚠️ REFERENCE |

---

## TASK-BASED FILE LOADING MATRIX

### Task 1: Generate Hook Only
**Load Order**:
1. 00_MASTER_INDEX.md (this file)
2. context.md → persona.md → psychology_of_content_instruction_guide.md
3. hook_principle.md → Instruction.md → hook_formulas.json
4. output-format.md
5. (Optional) Hook-Examples.md, visual-instruction.md

**Total Files**: 7 core + 2 optional = 9 files max

---

### Task 2: Generate Full Script Only (No Hook)
**Load Order**:
1. 00_MASTER_INDEX.md
2. context.md → persona.md → psychology_of_content_instruction_guide.md
3. script_structure.md → script_formulas.json → transition_techniques.md
4. output-format.md (adapt for script)
5. (Optional) script_examples.md

**Total Files**: 7 core + 1 optional = 8 files max

---

### Task 3: Generate Hook + Full Script (FULL VIDEO)
**Load Order**:
1. 00_MASTER_INDEX.md
2. **Foundation** (3): context.md → persona.md → psychology_of_content_instruction_guide.md
3. **Hook** (4): hook_principle.md → Instruction.md → hook_formulas.json → output-format.md
4. **Script** (3): script_structure.md → script_formulas.json → transition_techniques.md
5. (Optional) Hook-Examples.md, script_examples.md, visual-instruction.md

**Total Files**: 10 core + 3 optional = 13 files max

---

## AI SELF-CHECK PROTOCOL (Anti-Miss Mechanism)

Before generating ANY content, AI must answer these questions:

### Pre-Generation Checklist:
I have loaded 00_MASTER_INDEX.md: [YES/NO]

I have loaded all FOUNDATION files (context, persona, psychology): [YES/NO]

I understand the target audience from context.md: [YES/NO]

I understand Professor Simon's voice from persona.md: [YES/NO]

For HOOK task: I have loaded hook_principle.md, Instruction.md, hook_formulas.json: [YES/NO]

For SCRIPT task: I have loaded script_structure.md, script_formulas.json, transition_techniques.md: [YES/NO]

I have loaded output-format.md for structure requirements: [YES/NO]

text

If ANY answer is NO → STOP and request missing files.

---

## VERSION CONTROL

| Version | Date | Changes | Files Added/Modified |
|---------|------|---------|---------------------|
| 1.0 | 17/01/2026 | Initial hook system | Hook files only |
| 2.0 | 23/01/2026 | Added script system | Script files added |

---

## EMERGENCY FALLBACK

If AI is unsure which files to load:
1. **Always start with**: 00_MASTER_INDEX.md
2. **Always load Foundation trio**: context.md, persona.md, psychology_of_content_instruction_guide.md
3. **Check task type in prompt** → Load corresponding section files
4. **When in doubt**: Ask user to clarify task type

Layer 2: Structured Prompt Template (Force AI to Declare)
Khi bạn prompt AI, dùng format này:

text
# TASK: Generate [Hook Only / Script Only / Hook + Script]

## STEP 1: FILE LOADING DECLARATION (REQUIRED)
Before you generate anything, you MUST:

1. Confirm you have read 00_MASTER_INDEX.md
2. List ALL files you have loaded for this task
3. For each file, state ONE key insight you extracted

**Format**:
✅ context.md - Key insight: [Target audience is...]
✅ persona.md - Key insight: [Professor Simon uses...]
✅ hook_principle.md - Key insight: [Dopamine technique X works because...]
[Continue for all files]

**If you cannot list insights, STOP and request the missing files.**

---

## STEP 2: VALIDATION CHECKLIST
Before generating, check:

### For Hook Generation:
- [ ] Hook uses dopamine technique from hook_principle.md?
- [ ] Hook follows formula from hook_formulas.json?
- [ ] Hook does NOT reveal product name?
- [ ] Hook targets pain point from context.md?
- [ ] Hook uses Professor Simon voice from persona.md?

### For Script Generation:
- [ ] Script structure matches script_structure.md?
- [ ] Transitions follow transition_techniques.md?
- [ ] Product intro at 45-55s only?
- [ ] Body applies psychology principles?
- [ ] CTA includes catchphrase from persona.md?
- [ ] Using formula from script_formulas.json? → Follow formula timing exactly
- [ ] Creating new script? → Use script_structure.md as baseline (±5s flexibility OK)

**Declare your checklist results BEFORE generating content.**

---

## STEP 3: GENERATE CONTENT

[Now proceed with generation]

---

## PRODUCT/TOPIC INPUT

[Your product/topic details here]
Effect: AI phải tự kiểm tra và declare nó đã đọc gì → Bạn catch được ngay nếu nó miss file nào

Layer 3: Modular File Design (Reduce Overwhelm)
Thay vì dump 15 files cùng lúc, structure files thành modules:

Option A: Create "Combo Files" cho specific tasks
File mới: _COMBO_hook_generation.md

text
# COMBO FILE: Hook Generation Only
**Auto-includes**: context.md, persona.md, hook_principle.md, hook_formulas.json, output-format.md

[Content tóm tắt key points từ 5 files trên, organized theo task flow]

## Section 1: Audience & Pain Points (from context.md)
[Key pain points extracted]

## Section 2: Voice Requirements (from persona.md)
[Xưng hô, tone, catchphrase]

## Section 3: Dopamine Techniques (from hook_principle.md)
[8 techniques summary]

## Section 4: Hook Formulas (from hook_formulas.json)
[Top 5 proven formulas]

## Section 5: Output Format (from output-format.md)
[13-subsection structure]
Benefit:

Giảm từ 10 files → 1 combo file

AI chỉ cần đọc 1 file nhưng vẫn có đủ info

Dễ maintain consistency

Tradeoff:

Phải maintain 2 versions (individual files + combo)

Combo file có thể dài (nhưng vẫn < individual files combined)

Option B: Priority Tagging trong file names
Rename files với priority:

text
[P0] = Must read (Foundation)
[P1] = Must read for task
[P2] = Reference only
[P3] = Post-publish only

Examples:
[P0]_context.md
[P0]_persona.md
[P0]_psychology_of_content_instruction_guide.md
[P1-HOOK]_hook_principle.md
[P1-HOOK]_hook_formulas.json
[P1-SCRIPT]_script_structure.md
[P2]_visual-instruction.md
[P3]_metrics_evaluation.md
Trong prompt, bạn chỉ cần nói:

text
"Load all [P0] files + all [P1-HOOK] files for this hook generation task"
AI sẽ biết chính xác phải đọc files nào.

Layer 4: Output Validation (Post-Generation Check)
Sau khi AI generate, dùng checklist này để verify:

text
# POST-GENERATION VALIDATION CHECKLIST

## A. File Coverage Check
Review the output and verify AI applied guidelines from:

### Foundation Files:
- [ ] **context.md**: Hook/script addresses specific pain point listed?
- [ ] **persona.md**: Uses correct xưng hô (Tôi/Bạn/Anh)?
- [ ] **persona.md**: Includes catchphrase in outro?
- [ ] **psychology_of_content_instruction_guide.md**: Applies 2+ psychology principles?

### Hook Files (if hook generated):
- [ ] **hook_principle.md**: Uses stated dopamine technique correctly?
- [ ] **Instruction.md**: Hook is 2-10s, no product name reveal?
- [ ] **hook_formulas.json**: Follows structure of selected formula?
- [ ] **output-format.md**: Includes all 13 subsections?

### Script Files (if script generated):
- [ ] **script_structure.md**: Follows 5-phase structure (Hook→Transition→Body→Product→Outro)?
- [ ] **script_formulas.json**: Body uses proven formula pattern?
- [ ] **transition_techniques.md**: Smooth hook-to-body transition?
- [ ] **script_structure.md**: Product intro timing at 45-55s?

### Visual Files (if visual direction included):
- [ ] **visual-instruction.md**: Follows 70/30 engagement vs relevance rule?
- [ ] **visual-instruction.md**: Uses strategic mismatch technique?

## B. Quality Gates

If ANY checkbox is unchecked:
1. Identify which file's guideline was missed
2. Re-prompt AI with: "You missed guidelines from [file]. Please revise and apply [specific guideline]."
3. Re-validate until all checks pass

## C. Missing File Detection

If output feels generic or doesn't match brand:
- **Likely cause**: AI didn't fully read persona.md or context.md
- **Fix**: Re-prompt with: "Before you continue, quote 3 pain points from context.md and Professor Simon's xưng hô system from persona.md."