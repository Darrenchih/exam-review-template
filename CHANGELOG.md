# 更新紀錄 / Changelog

## [1.2.0] - 2026-10-04

### 新增
- CI 自動驗證（`.github/workflows/validate.yml`）：push 時檢查 5 個 HTML 的
  JS 語法、`T()`/`STR_EN` 存在性、`</html>` 結尾、demo 資料計數
- `CONTRIBUTING.md` 貢獻指南（中英雙語）
- `KNOWN_ISSUES.md` 已知問題追蹤

### 修復
- 練習模式 `WCTX.mode` 未設定導致答案按鈕無反應
- 「清除全部進度」按鈕轉義錯誤
- 模擬考 `renderEQ` 硬編碼中文，補 `STR_EN`（交卷、題號導覽）
- 英文版 HVAC123 殘留字串

## [1.1.0] - 2026-10-04

### 新增
- GitHub Pages 線上演示
- `.gitignore`、Issue 模板、PR 模板
- `README_EN.md` 英文版說明
- MIT 授權（LICENSE）

## [1.0.0] - 2026-10-04

### 新增
- 初始版本：考試複習網站模板
- 4 套語言版本（全英文 / 全中文 / 中文為主 / 英文為主）
- 4 套 AI 指令（`prompts/`）
- `WORKFLOW.md` 可複製流程、`DATA_FORMAT.md` 資料格式說明
- 完整引擎功能：學習/練習/模擬考/錯題本/自適應/雙語/主題/快捷鍵/列印/本地儲存
