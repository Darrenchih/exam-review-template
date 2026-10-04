# 可複製流程：為新科目生成考試複習網站

## 一句話版本

> 選一套語言 → 唸對應提示詞給 AI → AI 生成 → 驗證 → 交付

## 四套對照

| | 全英文 | 全中文 | 中英混雜（中文為主） | 中英混雜（英文為主） |
|---|---|---|---|---|
| HTML | `variants/template-en.html` | `variants/template-zh.html` | `variants/template-zh-mixed.html` | `variants/template-en-mixed.html` |
| 提示詞 | `prompts/PROMPT_EN.md` | `prompts/PROMPT_ZH.md` | `prompts/PROMPT_ZH_MIXED.md` | `prompts/PROMPT_EN_MIXED.md` |
| UI 語言 | 英文（鎖定） | 中文（鎖定） | 中文預設，可切英文 | 英文預設，可切中文 |
| 題目語言 | 英文 | 中文 | 中文為主 | 英文為主 |
| 適用場景 | 英文考試、國際證照 | 中文考試、國內證照 | 中文學習、英文術語 | 英文考試、中文輔助 |

## 詳細步驟

### Step 1：選語言版本

根據考試語言選擇上表中的一套。拿不準時：
- 考試用英文出題 → 英文為主
- 考試用中文出題 → 中文為主
- 只想練英文 → 全英文
- 只想看中文 → 全中文

### Step 2：給 AI 指令

把對應 `prompts/` 下的提示詞全文貼給任何 AI agent，
再加一句：

> 「科目是 [科目名稱]，範圍是 [考試範圍]」

AI 會按提示詞的 Phase 1-5 執行：確認範圍 → 生成知識點 → 填入模板 → 驗證 → 交付。

### Step 3：檢查交付

收到 HTML 後確認：
- [ ] 題數符合預期（預設 60-100）
- [ ] 每個選項都有專屬解析（點一題答錯看看）
- [ ] 中英切換正常（混雜版）
- [ ] 無亂碼、無空白頁面

### Step 4：迭代優化

不滿意的地方直接告訴 AI，例如：
- 「第 3 章的題目太簡單，加 10 題難題」
- 「知識卡的區別欄位再詳細一點」
- 「加 20 題情境題」

AI 會增量更新後重新交付。

## 目錄結構

```
exam-review-template/
├── README.md                 # 本文件
├── WORKFLOW.md               # 可複製流程（本文件）
├── DATA_FORMAT.md            # 資料格式參考
├── template.html             # 基礎模板（英文為主混雜）
├── variants/
│   ├── template-en.html         # 全英文
│   ├── template-zh.html         # 全中文
│   ├── template-zh-mixed.html   # 中英混雜（中文為主）
│   └── template-en-mixed.html   # 中英混雜（英文為主）
└── prompts/
    ├── PROMPT_EN.md             # 全英文指令
    ├── PROMPT_ZH.md             # 全中文指令
    ├── PROMPT_ZH_MIXED.md       # 中文為主指令
    └── PROMPT_EN_MIXED.md       # 英文為主指令
```

## 注意事項

1. **localStorage key 唯一**：每個科目用不同的 key（如 `math101_en_v1`），否則進度會互相覆蓋。
2. **引擎不動**：4 套 HTML 的引擎完全相同，只差語言設定與資料。
3. **資料品質**：AI 生成的題目要抽查，特別是專業科目的數字與公式。
