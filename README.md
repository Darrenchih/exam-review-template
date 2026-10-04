# 考試複習網站模板

[English version](README_EN.md)

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

> 🌐 **線上試用**：https://darrenchih.github.io/exam-review-template/

## 這是什麼

一個**單一 HTML 檔案**的離線考試複習網站：8 種複習模式（學習、練習、模擬考、弱點複習、錯題本、關鍵數字、公式訓練、考試辨識），進度自動存在你的瀏覽器裡。**不用安裝、不用連網、不用伺服器**，下載後雙擊即用。

想為自己的科目做一個？**複製一段話貼給任何 AI 就行**，剩下的 AI 會自己處理（見下方「為你的科目生成一個」）。

## 立即試用

- **線上**：點上面的 demo 連結，四套語言版本任選其一
- **本機**：下載任一 `variants/*.html`，用瀏覽器打開即可

> Demo 是精簡展示版：12 題（9 選擇＋3 是非）、5 張知識卡、4 個關鍵數字、1 個公式、4 組辨識，內容為「八大行星」範例資料。正式生成的版本為 60–100 題。

## 功能一覽（4 套相同）

- 📖 學習模式（知識卡：定義/作用/機制/區別/必背/陷阱）
- ✏️ 練習模式（自適應選題、每選項專屬解析）
- 📝 模擬考模式（計時、統一交卷、鍵盤快捷鍵）
- 🎯 弱點複習（spaced repetition）｜❌ 錯題本｜⭐ 收藏
- 🔢 關鍵數字｜📐 公式訓練｜🔍 考試辨識
- 📊 學習檔案（趨勢圖、強弱項、考試倒數）
- 💾 本地儲存 + JSON 匯出/匯入｜🖨️ 列印｜🌙 三種主題（淺色/深色/自動）

## 預覽截圖

下圖為 demo 的範例資料畫面：

| 全英文 | 全中文 |
|--------|--------|
| ![英文版 Dashboard](screenshots/en-dashboard.png) | ![中文版 Dashboard](screenshots/zh-dashboard.png) |

| 中英混雜（中文為主） | 中英混雜（英文為主） |
|----------------------|----------------------|
| ![中文為主 Dashboard](screenshots/zh-mixed-dashboard.png) | ![英文為主 Dashboard](screenshots/en-mixed-dashboard.png) |

## 為你的科目生成一個

**兩步，沒用過 AI 也會：**

1. **複製下面這段話**（把「全中文」換成你要的版本：全中文／全英文／中文為主／英文為主）
2. **貼給任何 AI**（ChatGPT、Claude、Muse……都行），之後按它問的回答就好

```
我想用這個模板為我的考試科目生成一個複習網站。

倉庫：https://github.com/Darrenchih/exam-review-template
我要的語言版本：全中文（四選一：全中文／全英文／中文為主／英文為主）

請你：
1. 從倉庫讀取對應的提示詞（prompts/）、HTML 模板（variants/）和 DATA_FORMAT.md：
   - 全中文 → prompts/PROMPT_ZH.md ＋ variants/template-zh.html
   - 全英文 → prompts/PROMPT_EN.md ＋ variants/template-en.html
   - 中文為主 → prompts/PROMPT_ZH_MIXED.md ＋ variants/template-zh-mixed.html
   - 英文為主 → prompts/PROMPT_EN_MIXED.md ＋ variants/template-en-mixed.html
2. 按照提示詞的 Phase 1 先跟我確認科目名稱和考試範圍，再繼續後面步驟。
```

AI 會自己去倉庫讀檔，先跟你確認科目和範圍，再研究、生成 60–100 題、填入模板、驗證後交付。**你不需要下載任何檔案**，也不用懂 AI。

## 四套語言版本

| 版本 | HTML | 提示詞 | 說明 | 適用場景 |
|------|------|--------|------|----------|
| 全英文 | `variants/template-en.html` | `prompts/PROMPT_EN.md` | UI＋題目全英文，語言鎖定 | 英文考試、國際證照 |
| 全中文 | `variants/template-zh.html` | `prompts/PROMPT_ZH.md` | UI＋題目全中文，語言鎖定 | 中文考試、國內證照 |
| 中英混雜（中文為主） | `variants/template-zh-mixed.html` | `prompts/PROMPT_ZH_MIXED.md` | 中文預設，可切英文 | 中文學習、英文術語 |
| 中英混雜（英文為主） | `variants/template-en-mixed.html` | `prompts/PROMPT_EN_MIXED.md` | 英文預設，可切中文 | 英文考試、中文輔助 |

## 文件

| 檔案 | 說明 |
|------|------|
| `WORKFLOW.md` | 可複製流程：選語言→給指令→驗證→交付→迭代 |
| `DATA_FORMAT.md` | 9 種資料結構的欄位說明 |
| `CONTRIBUTING.md` | 貢獻指南（中英雙語） |
| `KNOWN_ISSUES.md` | 已知問題追蹤 |
| `DISCLAIMER.md` | 免責聲明（中英雙語） |
| `CHANGELOG.md` | 版本更新紀錄 |
| `template.html` | 基礎模板（英文為主混雜） |
| `variants/` | 4 套 HTML |
| `prompts/` | 4 套 AI 指令 |

## 常見問題

**Q：打開是空白頁？**
A：用 Chrome／Edge／Safari 開啟，並確認已啟用 JavaScript。直接雙擊 HTML 檔即可，不需要架伺服器。

**Q：我的進度存在哪裡？會上傳嗎？**
A：只存在你瀏覽器的 localStorage，不會上傳到任何伺服器。換瀏覽器或清除網站資料會遺失，請用站內的「匯出進度檔（JSON）」備份。

**Q：Demo 怎麼只有 12 題？**
A：Demo 是精簡展示版。用提示詞正式生成的版本為 60–100 題。

**Q：多個科目的進度會互相覆蓋嗎？**
A：如果 localStorage key 相同就會。每個科目請用不同的 key（例如 `math101_en_v1`），詳見 `WORKFLOW.md` 注意事項。

**Q：全英文／全中文版沒有語言切換鈕？**
A：正常，這兩個版本鎖定單一語言。需要切換請用混雜版。

**Q：AI 生成的題目可以直接拿去考試嗎？**
A：不行。AI 生成內容務必抽查，特別是專業科目的數字與公式，一律以你的教材和課堂講授為準。詳見 [免責聲明](DISCLAIMER.md)。

## 免責聲明

要點：AI 生成內容可能有誤，請對照教材核實；本專案僅為學習輔助工具，不保證考試結果；與任何學校或考試機構無關；風險自負。完整內容見 [DISCLAIMER.md](DISCLAIMER.md)。

## 授權

MIT — 詳見 [LICENSE](LICENSE)。歡迎自由複製、使用、修改、分享。
