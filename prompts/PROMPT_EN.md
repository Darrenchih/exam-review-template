# Instruction: Generate an All-English Exam Review Website

> Self-contained instruction. Any AI agent can complete this task after reading
> this file, `../variants/template-en.html`, and `../DATA_FORMAT.md`.
>
> **Core principle**: The website engine is IDENTICAL to the template.
> Only the knowledge content differs. The AI researches the subject and
> generates all learning materials.

---

## Task

Generate an **all-English** exam review website for a user-specified subject,
based on `../variants/template-en.html`.

**Language rules (strict):**
- ALL UI text in English. No Chinese characters anywhere in UI.
- ALL questions, options, explanations in English.
- Knowledge cards: English only (`def`, `fn`, `how`, `cmp`, `nums`, `mis`).
  The `_en` fields may mirror the base fields or be omitted.
- The `EN` translation map: still required structurally, but English content
  goes directly in base fields. Set `EN={}` empty is NOT allowed to break;
  fill base fields in English and provide minimal EN entries.
- No language toggle button (already removed in template).

## Prerequisites

1. Read `../variants/template-en.html` (note data section comments).
2. Read `../DATA_FORMAT.md` (field specifications).

## Workflow

### Phase 1: Confirm scope

| Question | Example |
|----------|---------|
| Subject name (English) | Organic Chemistry |
| Exam scope | Midterm Chapters 1-5 |
| Question count | Default 60-100 |
| Source materials | If provided, use them; otherwise use AI knowledge |

Set localStorage key: lowercase English + version (e.g., `organic_chem_en_v1`).

### Phase 2: Generate content (AI-researched)

**Quality standards (non-negotiable):**

#### Categories (3-8)
Cover the exam's main chapters. `{id, zh, en}` — `zh` may repeat `en` or be omitted gracefully (engine falls back to `en`).

#### Knowledge cards (3-8 per category)
Every field filled in English:
- `term`: English term
- `def`: precise definition
- `fn`: function/purpose
- `how`: mechanism (first principles)
- `cmp`: distinction from confusable concepts (exam traps)
- `nums`: must-memorize facts (or `[]`)
- `mis`: common misconceptions (or `[]`)

#### Questions (60-100, MC:TF ≈ 5:1)

**Multiple choice — every question MUST have:**
- `q`: question in English
- `opts`: 4 options; distractors must be **plausible wrong answers**
  (common misconceptions, similar concepts, number confusion).
  No obviously absurd fillers. No "all of the above" padding.
- `a`: correct index
- `oe`: **dedicated explanation per option** (4 entries, aligned with opts)
- `exp`: overall explanation
- `cc`: one-line confusion warning
- `dif`: 1 (40%) / 2 (40%) / 3 (20%)
- `keys`: keywords array

**True/False:**
- Single unambiguous factual judgment. `exp` explains the basis.

**Coverage:** every card ≥ 2-3 questions; ≥15% scenario-based; key numbers tested as questions.

#### EN map
Fill base fields in English; provide EN entries mirroring them
(or minimal entries — engine requires the structure).

#### NUMBERS / FORMULAS / RECOG
- Numbers: must-memorize constants for the exam
- Formulas: with working `gen()` for auto-generated practice, or `[]`
- Recognition: high-frequency cue→answer pairs

### Phase 3: Fill template

```bash
cp ../variants/template-en.html ~/workspace/your_files/<subject>/<file>.html
```

1. Brand replacement: subject name, `examreview_en_v1` → your key.
2. Replace 8 data sections (boundaries in DATA_FORMAT.md).
3. Do NOT delete: `const DATA_V`, helpers (`catName/kpName/kDef/...`),
   `ERRTYPES`, `KP_LEVEL_*`.

### Phase 4: Validate (mandatory)

- `node --check` on extracted script
- Programmatic: every `q.kp` ∈ KPS, `q.cat` ∈ CATS, `len(oe)==len(opts)`, no duplicate ids, EN covers all question ids
- Smoke test: render dash/map/study/practice/wrong/nums/formulas/recog with no errors
- **No Chinese characters** in UI strings or questions (scan for CJK range)

### Phase 5: Deliver

- Attach HTML via `sandbox://` link
- Report: categories, cards, question count, validation results, sources

## Prohibited

- Do not modify engine logic (102 functions, adaptive algorithm, UI)
- Do not fabricate uncertain専門 content (verify or flag)
- Do not skip `oe` per-option explanations
- Do not reuse another subject's localStorage key
