# Exam Review Website Template

[中文版](README.md)

A generic template based on the complete engine of the HVAC 123 review website.
Websites generated from it are **functionally identical** to the original —
only the knowledge content differs.

## Four Language Variants

| Variant | HTML | Prompt | Description |
|---------|------|--------|-------------|
| All English | `variants/template-en.html` | `prompts/PROMPT_EN.md` | UI + questions all English, no toggle |
| All Chinese | `variants/template-zh.html` | `prompts/PROMPT_ZH.md` | UI + questions all Chinese, no toggle |
| Mixed (Chinese primary) | `variants/template-zh-mixed.html` | `prompts/PROMPT_ZH_MIXED.md` | Chinese default, switchable to English |
| Mixed (English primary) | `variants/template-en-mixed.html` | `prompts/PROMPT_EN_MIXED.md` | English default, switchable to Chinese |

## Files

| File | Description |
|------|-------------|
| `README_EN.md` | This file |
| `README.md` | Chinese version |
| `WORKFLOW.md` | **Replicable workflow**: pick language → give instruction → verify → deliver → iterate |
| `DATA_FORMAT.md` | Field specifications for all 9 data structures |
| `template.html` | Base template (English-primary mixed) |
| `variants/` | 4 HTML variants |
| `prompts/` | 4 AI instructions |
| `LICENSE` | MIT License — everyone is free to copy, modify, and distribute |

## Usage

### Just two steps next time

1. Read `WORKFLOW.md` and pick a language variant
2. Paste the corresponding prompt from `prompts/` to any AI, adding "the subject is ○○"

The AI will research the subject, generate knowledge content, fill the template,
validate, and deliver — automatically.

## Engine Features (identical across all 4 variants)

- 📖 Study mode (knowledge cards: definition / function / mechanism / distinction / key facts / traps)
- ✏️ Practice mode (adaptive question selection, per-option explanations)
- 📝 Mock exam mode (timer, unified submit, keyboard shortcuts)
- 🎯 Weak review (spaced repetition)｜❌ Mistake log｜⭐ Favorites
- 🔢 Critical numbers｜📐 Formula trainer｜🔍 Exam recognition
- 📊 Learning profile (trend chart, strengths/weaknesses, exam countdown)
- 💾 Local storage + JSON export/import｜🖨️ Print｜🌙 3 themes

## License

MIT — see [LICENSE](LICENSE). Everyone is free to copy, use, modify, and share.
