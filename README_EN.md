# Exam Review Website Template

[中文版](README.md)

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

> 🌐 **Live demo**: https://darrenchih.github.io/exam-review-template/

## What Is This

A **single-file, offline** exam review website: 8 study modes (study, practice, mock exam, weak review, mistake log, critical numbers, formula trainer, exam recognition) with progress saved automatically in your browser. **No install, no internet, no server required** — download and double-click to use.

Want one for your own subject? Paste an instruction from `prompts/` to any AI. It will confirm the scope with you first, then research the subject, generate 60–100 questions, and deliver the finished site. The prompts are self-contained: any person's any AI agent can run them with no background knowledge.

## Try It Now

- **Online**: click the demo link above and pick any of the 4 language variants
- **Local**: download any `variants/*.html` and open it in your browser

> The demo is a trimmed showcase: 12 questions (9 multiple-choice + 3 true/false), 5 knowledge cards, 4 critical numbers, 1 formula, 4 recognition items, using "Eight Planets" sample data. Properly generated sites contain 60–100 questions.

## Features (identical across all 4 variants)

- 📖 Study mode (knowledge cards: definition / function / mechanism / distinction / key facts / traps)
- ✏️ Practice mode (adaptive question selection, per-option explanations)
- 📝 Mock exam mode (timer, unified submit, keyboard shortcuts)
- 🎯 Weak review (spaced repetition)｜❌ Mistake log｜⭐ Favorites
- 🔢 Critical numbers｜📐 Formula trainer｜🔍 Exam recognition
- 📊 Learning profile (trend chart, strengths/weaknesses, exam countdown)
- 💾 Local storage + JSON export/import｜🖨️ Print｜🌙 3 themes (light/dark/auto)

## Screenshots

Sample data shown:

| All English | All Chinese |
|-------------|-------------|
| ![English Dashboard](screenshots/en-dashboard.png) | ![Chinese Dashboard](screenshots/zh-dashboard.png) |

| Mixed (Chinese primary) | Mixed (English primary) |
|-------------------------|-------------------------|
| ![Chinese-primary Dashboard](screenshots/zh-mixed-dashboard.png) | ![English-primary Dashboard](screenshots/en-mixed-dashboard.png) |

## Generate One for Your Subject

Two steps (full process in `WORKFLOW.md`):

1. **Pick a language variant** from the table below. When unsure, match the language your exam is written in.
2. **Give the instruction to AI**: paste the full prompt from the matching `prompts/` file to any AI agent, adding "the subject is [subject name], covering [scope]".

The AI will **confirm the scope with you first** (Phase 1), then research, generate all knowledge content (60–100 questions, per-option explanations, full knowledge-card fields), fill the template, validate, and deliver. The engine logic should not be modified.

## Four Language Variants

| Variant | HTML | Prompt | Description | Best for |
|---------|------|--------|-------------|----------|
| All English | `variants/template-en.html` | `prompts/PROMPT_EN.md` | UI + questions all English, language locked | English exams, international certifications |
| All Chinese | `variants/template-zh.html` | `prompts/PROMPT_ZH.md` | UI + questions all Chinese, language locked | Chinese exams, domestic certifications |
| Mixed (Chinese primary) | `variants/template-zh-mixed.html` | `prompts/PROMPT_ZH_MIXED.md` | Chinese default, switchable to English | Studying in Chinese, English terminology |
| Mixed (English primary) | `variants/template-en-mixed.html` | `prompts/PROMPT_EN_MIXED.md` | English default, switchable to Chinese | English exams with Chinese support |

## Files

| File | Description |
|------|-------------|
| `WORKFLOW.md` | Replicable workflow: pick language → give instruction → verify → deliver → iterate |
| `DATA_FORMAT.md` | Field specifications for all 9 data structures |
| `CONTRIBUTING.md` | Contribution guide (bilingual) |
| `KNOWN_ISSUES.md` | Known issues tracker |
| `CHANGELOG.md` | Version history |
| `template.html` | Base template (English-primary mixed) |
| `variants/` | 4 HTML variants |
| `prompts/` | 4 AI instructions |

## FAQ

**Q: Blank page on open?**
A: Open with Chrome / Edge / Safari and make sure JavaScript is enabled. Just double-click the HTML file — no server needed.

**Q: Where is my progress stored? Is it uploaded?**
A: Only in your browser's localStorage — never uploaded anywhere. Switching browsers or clearing site data will erase it; use the in-site "Export progress (JSON)" to back up.

**Q: Why does the demo only have 12 questions?**
A: The demo is a trimmed showcase. Properly generated sites contain 60–100 questions.

**Q: Will progress for multiple subjects overwrite each other?**
A: Yes, if they share the same localStorage key. Use a unique key per subject (e.g. `math101_en_v1`); see `WORKFLOW.md` notes.

**Q: No language toggle in the All-English / All-Chinese variant?**
A: By design — those two variants lock a single language. Use a mixed variant if you need switching.

**Q: Can I use AI-generated questions directly for my exam?**
A: No. Always spot-check AI output — especially numbers and formulas in technical subjects — against your course materials and classroom instruction.

## License

MIT — see [LICENSE](LICENSE). Everyone is free to copy, use, modify, and share.
