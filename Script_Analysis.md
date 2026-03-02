# TASK: Analyze Script & Generate Formula Entry

## LOAD FILES
- context.md
- persona.md
- psychology_of_content_instruction_guide.md
- script_formulas.json (nếu có)

---

## INPUT

**Video URL:** [paste link]

**Topic:** [chủ đề]

**Product_Include:** [True/False]

**Product_Name (nếu có):** [tên]

**Performance (nếu có):**
- Views: 
- Retention: 
- Engagement: 

**Full Script:**

---

## OUTPUT

### 1. TIMING BREAKDOWN

**[0-10s] HOOK:**
[text]

**[10-15s] TRANSITION:**
[text]

**[15-25s] BODY CHUNK 1:**
[text]

**[25-35s] BODY CHUNK 2:**
[text]

**[35-45s] BODY CHUNK 3:**
[text]

**[45-55s] PHASE 4:**
[text - Advanced Tip hay Product?]

**[55-60s] OUTRO:**
[text]

---

### 2. PATTERN ANALYSIS

**Hook Pattern:**
- Type: [Question/Stat/Story/Contradiction]
- Dopamine Technique: [từ psychology guide]
- Closest Hook Formula: [CG-001, PI-001, etc.]

**Body Structure:**
- Chunks: [2/3/4]
- Chunk themes: [list themes]

**Phase 4 Type:** [Advanced Tip / Product Intro / Other]

**Outro:** 
- Catchphrase: [Yes/No]
- CTA: [type]

**Closest Existing Formula:** [SF-001 / SF-002 / None]

**Unique Elements:** [gì khác biệt so với existing formulas]

---

### 3. TEMPLATE EXTRACTION

**Transition Template:**
`[template với [variables]]`

**Body Chunk 1 Template:**
`[template với [variables]]`

**Body Chunk 2 Template:**
`[template với [variables]]`

**Body Chunk 3 Template:**
`[template với [variables]]`

**Phase 4 Template:**
`[template với [variables]]`

**Outro Template:**
`[template với [variables]]`

**Variables:**
- `[var1]`: [description, examples]
- `[var2]`: [description, examples]
- ...

---

### 4. PSYCHOLOGY CHECK

- Trust Ladder Levels: [1→2→3→4→5?]
- Information Chunks: [2/3/4]
- Open Loop Strategy: [mô tả]
- Dopamine Techniques: [list]
- Pattern Variations: [có thay đổi mỗi 10s không?]

---

### 5. BRAND VOICE MATCH

- Xưng hô: [Tôi/Mình? Bạn/Anh?]
- Tone: [Authoritative/Empathetic/Other]
- Catchphrase: [có/không, text gì]
- Alignment: [High/Medium/Low với persona.md]
- Adjustments Needed: [list nếu có]

---

### 6. WHY IT WORKS

**Strengths:**
1. [strength 1]
2. [strength 2]
3. [strength 3]

**Weaknesses:**
1. [weakness 1 nếu có]

**Performance Hypothesis:** [dự đoán perform với audience trong context.md]

---

### 7. FORMULA ENTRY JSON

```json
{
  "id": "SF-XXX",
  "name": "[tên pattern]",
  "category": "[Educational/Product/Hybrid/Story]",
  "product_include": [true/false],
  "scope": "10-60s (Body only)",
  
  "hook_compatibility": {
    "works_well_with": ["[list hook formulas]"],
    "note": "[giải thích]"
  },

  "timing_structure": {
    "transition": "10-15s",
    "body_chunk_1": "15-25s",
    "body_chunk_2": "25-35s",
    "body_chunk_3": "35-45s",
    "phase_4": "45-55s",
    "outro": "55-60s"
  },

  "psychology_applied": {
    "trust_ladder_levels":,[1][2][3]
    "information_chunks": 3,
    "open_loop_strategy": "[mô tả]",
    "dopamine_maintenance": ["[techniques]"]
  },

  "phase_templates": {
    "transition_10_15s": {
      "template": "[template]",
      "variables": {
        "[var_name]": {
          "examples": ["[ex1]", "[ex2]"],
          "note": "[note]"
        }
      },
      "example": "[example từ script gốc]"
    },
    
    "body_chunk_1_15_25s": {
      "theme": "[theme]",
      "template": "[template]",
      "variables": {},
      "example": "[example]"
    },
    
    "body_chunk_2_25_35s": {
      "theme": "[theme]",
      "template": "[template]",
      "variables": {},
      "example": "[example]"
    },
    
    "body_chunk_3_35_45s": {
      "theme": "[theme]",
      "template": "[template]",
      "variables": {},
      "example": "[example]"
    },
    
    "phase_4_45_55s": {
      "type": "[Advanced Tip / Product Intro]",
      "template": "[template]",
      "variables": {},
      "example": "[example]"
    },
    
    "outro_55_60s": {
      "template": "[template]",
      "variables": {},
      "example": "[example]"
    }
  },

  "examples": [
    {
      "topic": "[topic gốc]",
      "product_include": [true/false],
      "filled_body_script": {
        "transition_10_15s": "[text]",
        "chunk_1_15_25s": "[text]",
        "chunk_2_25_35s": "[text]",
        "chunk_3_35_45s": "[text]",
        "phase_4_45_55s": "[text]",
        "outro_55_60s": "[text]"
      },
      "video_id": "[link]",
      "performance": {
        "views": null,
        "retention": null,
        "engagement": null
      },
      "classification": "[WINNER/TEST/null]",
      "notes": "[insights]"
    }
  ],

  "comparison_wrong": {
    "filled_body_script": {
      "[phase_name]": "[bad example]"
    },
    "why_fails": "[explanation]"
  },

  "best_for": [
    "[use case 1]",
    "[use case 2]"
  ],

  "avoid_for": [
    "[scenario 1]",
    "[scenario 2]"
  ],

  "constraints": [
    "[constraint 1]",
    "[constraint 2]"
  ],

  "success_rate": null,
  "total_tests": 0
}
