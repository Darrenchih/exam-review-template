# 通用指令：生成中英混雜（中文為主）考試複習網站

> 自包含指令。任何 AI agent 讀完本文件、`../variants/template-zh-mixed.html`、
> `../DATA_FORMAT.md` 後即可獨立完成任務。
>
> **核心原則**：網站引擎與模板完全相同，唯一的差別是知識點內容。
> AI 負責研究科目並生成全部學習資料。

---

## 任務

為使用者指定的科目生成**中文為主、中英混雜**的考試複習網站，
基於 `../variants/template-zh-mixed.html`。

**語言規則：**
- UI 預設中文，可切換英文（保留語言切換按鈕）。
- 題目以中文為主，專有名詞保留英文原文括註（如「蒸發器（Evaporator）」）。
- 知識卡：中文欄位為主，`_en` 欄位提供英文對照（用於英文模式）。
- `EN` 翻譯表：提供英文版題目（供切換英文時使用）。
- 術語首次出現時中英並陳，之後可用中文簡稱。

## 前置閱讀

1. `../variants/template-zh-mixed.html`
2. `../DATA_FORMAT.md`

## 執行流程

### Phase 1：確認範圍

科目名稱（中/英）、考試範圍、目標題數（預設 60-100）、指定教材。
localStorage key：如 `subject_zhm_v1`。

### Phase 2：生成學習資料

**品質標準（不可打折）：**

#### 分類 CATS（3-8 個）
`{id, zh, en}` 中英對照。

#### 知識卡 KPS（每分類 3-8 張）
中英雙語欄位都要填：
- 中文：`def, fn, how, cmp, nums, mis`
- 英文：`def_en, fn_en, how_en, cmp_en, nums_en, mis_en`
- `term`（英文術語）+ `zh`（中文名）

#### 題目 QUESTIONS（60-100 題，選擇:是非 ≈ 5:1）
- `q`：中文題目，術語中英並陳
- `opts`：4 個選項（中文為主，術語保留英文）
- `oe`：每選項專屬中文解析
- `exp`/`cc`：中文解析與陷阱提醒
- `dif`：1（40%）/2（40%）/3（20%）
- 每張卡 ≥2-3 題，≥15% 情境題

#### EN 翻譯表
每題提供完整英文版（`q, o, e, c, k, w`），英文模式時使用。

#### 其他
NUMBERS（中英意義）、FORMULAS、RECOG（中英）、TS_IDS/PROC_IDS（可空）。

### Phase 3：填入模板

```bash
cp ../variants/template-zh-mixed.html ~/workspace/your_files/<科目>/<檔名>.html
```

品牌替換 + 8 個資料區替換。不可刪除通用常數。

### Phase 4：驗證

- `node --check`、資料完整性程式驗證、8 頁冒煙測試
- 中英文模式各渲染一次，確認無缺翻譯導致的空白

### Phase 5：交付

`sandbox://` 附件 + 報告（題數、驗證結果、資料來源）。

## 禁止事項

- 不得修改引擎邏輯｜不虛構不確定內容｜`oe` 不可省略
- localStorage key 不可重複｜干擾選項不可敷衍
