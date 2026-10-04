# Contributing / 貢獻指南

[English version below](#english)

## 歡迎貢獻

這個模板是 MIT 授權的開源專案，歡迎任何形式的貢獻：
修 bug、補翻譯、加功能、改善文件都可以。

## 基本原則

### 引擎 vs 資料的分界

- **引擎**（`template.html` 內的 JavaScript/CSS/HTML 結構）：
  修改會影響所有使用者，請先開 Issue 討論。
- **資料**（`QUESTIONS`、`KPS`、`NUMBERS`、`FORMULAS`、`RECOG` 等陣列）：
  各自科目自行填寫，不需要動引擎。

### 四個版本必須同步

`variants/` 下有 4 個 HTML，任何引擎層級的修改必須同步到
4 個檔案（或同步到 `template.html` 再重新產生 variants）。
CI（`.github/workflows/validate.yml`）會自動檢查 5 個檔案的語法與資料完整性。

## 提交流程

1. Fork 本倉庫
2. 開一個分支（`fix/xxx` 或 `feat/xxx`）
3. 修改後確認 CI 通過（`node --check`＋資料計數）
4. 發 Pull Request，說明改了什麼、為什麼

## 回報問題

請用 Issue 模板（Bug report / Feature request），附上：
- 使用的版本（en / zh / zh-mixed / en-mixed）
- 瀏覽器與作業系統
- 重現步驟
- 截圖（如果有）

---

## English

<a id="english"></a>

Contributions are welcome: bug fixes, translations, features, docs.

### Engine vs data

- **Engine** (JS/CSS/HTML structure in `template.html`): affects all users —
  please open an Issue to discuss first.
- **Data** (`QUESTIONS`, `KPS`, `NUMBERS`, `FORMULAS`, `RECOG`, …):
  fill in per subject; no engine changes needed.

### Keep the 4 variants in sync

Any engine-level change must be applied to all 4 files under `variants/`
(or to `template.html` then regenerate the variants).
CI (`.github/workflows/validate.yml`) checks syntax and data integrity
across all 5 HTML files automatically.

### Pull requests

1. Fork the repo
2. Create a branch (`fix/xxx` or `feat/xxx`)
3. Make sure CI passes
4. Open a PR describing what and why
