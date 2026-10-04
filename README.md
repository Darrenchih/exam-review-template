# 考試複習網站模板

[English version](README_EN.md)

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

> 🌐 **線上試用**：https://darrenchih.github.io/exam-review-template/

以 HVAC 123 複習網站的完整引擎為基礎製成的通用模板。
生成的網站與原系統**功能完全相同**，只差知識點內容。

## 四套語言版本

| 版本 | HTML | 提示詞 | 說明 |
|------|------|--------|------|
| 全英文 | `variants/template-en.html` | `prompts/PROMPT_EN.md` | UI+題目全英文，無切換 |
| 全中文 | `variants/template-zh.html` | `prompts/PROMPT_ZH.md` | UI+題目全中文，無切換 |
| 中英混雜（中文為主） | `variants/template-zh-mixed.html` | `prompts/PROMPT_ZH_MIXED.md` | 中文預設，可切英文 |
| 中英混雜（英文為主） | `variants/template-en-mixed.html` | `prompts/PROMPT_EN_MIXED.md` | 英文預設，可切中文 |

## 文件

| 檔案 | 說明 |
|------|------|
| `README.md` | 本文件 |
| `WORKFLOW.md` | **可複製流程**：選語言→給指令→驗證→交付→迭代 |
| `DATA_FORMAT.md` | 9 種資料結構的欄位說明 |
| `template.html` | 基礎模板（英文為主混雜） |
| `variants/` | 4 套 HTML |
| `prompts/` | 4 套 AI 指令 |
| `LICENSE` | MIT 授權 — 每個人都可自由複製、使用、修改、分享 |

## 使用方式

### 下次只需要兩步

1. 看 `WORKFLOW.md` 選一套語言
2. 把對應 `prompts/` 的提示詞貼給任何 AI，加一句「科目是○○」

AI 會自動研究科目、生成知識點、填入模板、驗證、交付。

## 引擎功能（4 套相同）

- 📖 學習模式（知識卡：定義/作用/機制/區別/必背/陷阱）
- ✏️ 練習模式（自適應選題、每選項專屬解析）
- 📝 模擬考模式（計時、統一交卷、鍵盤快捷鍵）
- 🎯 弱點複習（spaced repetition）｜❌ 錯題本｜⭐ 收藏
- 🔢 關鍵數字｜📐 公式訓練｜🔍 考試辨識
- 📊 學習檔案（趨勢圖、強弱項、考試倒數）
- 💾 本地儲存 + JSON 匯出/匯入｜🖨️ 列印｜🌙 三種主題
