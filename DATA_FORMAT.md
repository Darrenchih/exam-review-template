# 資料格式說明

> 本文件是 `PROMPT_TEMPLATE.md` Phase 2 的欄位參考。
> 資料由 AI 依品質標準生成，使用者無需手動填寫。

本文檔說明 `template.html` 中所有可修改的資料結構。

## 目錄

1. [CATS — 分類](#1-cats--分類)
2. [KPS — 知識卡](#2-kps--知識卡)
3. [QUESTIONS — 題庫](#3-questions--題庫)
4. [EN — 英文翻譯](#4-en--英文翻譯)
5. [NUMBERS — 關鍵數字](#5-numbers--關鍵數字)
6. [FORMULAS — 公式](#6-formulas--公式)
7. [RECOG — 考試辨識](#7-recog--考試辨識)
8. [TS_IDS / PROC_IDS](#8-ts_ids--proc_ids)
9. [ERRTYPES — 錯誤類型](#9-errtypes--錯誤類型)

---

## 1. CATS — 分類

```javascript
const CATS=[
  {id:"cat1", zh:"分類一", en:"Category One"},
  {id:"cat2", zh:"分類二", en:"Category Two"},
];
```

| 欄位 | 必填 | 說明 |
|------|------|------|
| id | ✓ | 唯一英文 ID，題目用 `cat` 關聯 |
| zh | ✓ | 中文名稱 |
| en | ✓ | 英文名稱 |

---

## 2. KPS — 知識卡

```javascript
const KPS=[
  {
    id:"sample_kp1",       // 唯一 ID
    cat:"cat1",            // 所屬分類 ID
    term:"Sample Term One", // 英文術語
    zh:"範例術語一",        // 中文名稱
    def:"中文定義",         // 是什麼
    def_en:"English definition",
    fn:"中文作用",          // 做什麼
    fn_en:"English function",
    how:"中文運作方式",     // 怎麼運作
    how_en:"English how",
    cmp:"中文區別",         // 與相似概念的區別
    cmp_en:"English distinction",
    nums:["要點一"],        // 必背要點（中文陣列）
    nums_en:["Key fact one"],
    mis:["陷阱一"],         // 常見陷阱（中文陣列）
    mis_en:["Trap one"],
    pre:["other_kp_id"],   // 前置知識點 ID（選填）
    img:"images/pic.png",  // 配圖路徑（選填）
  },
];
```

**注意**：`_en` 欄位若缺失，英文模式會顯示中文原文。

---

## 3. QUESTIONS — 題庫

### 選擇題 (mc)

```javascript
{
  id:"q1",              // 唯一 ID
  cat:"cat1",           // 分類 ID
  kp:"sample_kp1",      // 知識點 ID
  t:"mc",               // 題型
  q:"題目（中文）",
  opts:["選項A","選項B","選項C","選項D"],
  a:1,                  // 正確答案索引（0 起）
  oe:[                  // 每個選項的專屬解析（與 opts 一一對應）
    "選項A錯誤的原因",
    "正確：選項B正確的原因",
    "選項C錯誤的原因",
    "選項D錯誤的原因"
  ],
  exp:"整體解析",
  cc:"易混淆提醒",
  dif:1,                // 難度 1-3
  keys:["關鍵字"],       // 關鍵字陣列
}
```

### 是非題 (tf)

```javascript
{
  id:"q3", cat:"cat1", kp:"sample_kp1", t:"tf",
  q:"題目敘述",
  a:true,               // true/false
  exp:"解析",
  cc:"易混淆提醒",
  dif:1,
  keys:["關鍵字"],
}
```

**驗證規則**：
- 每題的 `kp` 必須對應到 KPS 中的 id
- 每題的 `cat` 必須對應到 CATS 中的 id
- 選擇題的 `oe` 長度必須等於 `opts` 長度
- `a` 必須是有效的索引

---

## 4. EN — 英文翻譯

題目預設顯示英文。若某題無英文版，則顯示中文原文。

```javascript
const EN={};
EN["q1"]={
  q:"English question",
  o:["opt1","opt2","opt3","opt4"],  // 選項英文（順序與中文一致）
  e:"English explanation",
  c:"English confusion note",
  k:["keyword"],                     // 關鍵字英文
  w:["why opt1 wrong", "correct: why opt2 right", ...], // oe 英文
};
EN["q3"]={
  q:"English true/false statement",
  e:"English explanation",
  c:"English confusion note",
  k:["keyword"],
};
```

---

## 5. NUMBERS — 關鍵數字

```javascript
const NUMBERS=[
  {n:"100", m:"中文意義", m_en:"English meaning", kp:"sample_kp1"},
];
// 無則設為空陣列
```

---

## 6. FORMULAS — 公式

可自動生成練習題的公式：

```javascript
const FORMULAS=[
  {
    id:"f1",
    name:"中文名",
    name_en:"English name",
    formula:"C = A + B",
    kp:"sample_kp1",
    gen(){
      const A=Math.floor(Math.random()*10)+1;
      const B=Math.floor(Math.random()*10)+1;
      const en=LANG==='en';
      return {
        q: en ? `A=${A}, B=${B}, find C` : `A=${A}，B=${B}，求 C`,
        a: A+B,       // 數字答案
        tol: 0.1,     // 容許誤差
        unit: "",     // 單位
        hint: `C = ${A} + ${B}`,
      };
    }
  },
];
```

---

## 7. RECOG — 考試辨識

快速記憶卡（看到提示就反應答案）：

```javascript
const RECOG=[
  {cue:"提示", cue_en:"English cue",
   a:"答案", a_en:"English answer",
   kp:"sample_kp1"},
];
```

---

## 8. TS_IDS / PROC_IDS

故障診斷 / 程序訓練模式用的題目 ID：

```javascript
const TS_IDS=["q1","q4"];   // 情境題 ID
const PROC_IDS=["q2"];       // 程序題 ID
// 無則設為空陣列
```

---

## 9. ERRTYPES — 錯誤類型

預設 10 種通用錯誤類型，一般不需修改：

```javascript
const ERRTYPES=[
  ["concept","概念錯","Concept error"],
  ["definition","定義錯","Definition error"],
  ["calculation","計算錯","Calculation error"],
  ["unit","單位錯","Unit error"],
  ["procedure","程序錯","Procedure error"],
  ["sequence","順序錯","Sequence error"],
  ["location","位置錯","Location error"],
  ["terminology","術語錯","Terminology error"],
  ["recognition","題目辨識錯","Recognition error"],
  ["careless","粗心錯","Careless error"],
];
```

---

## 檢查清單

填入資料後，確認：

- [ ] 所有題目的 `kp` 都有對應的知識卡
- [ ] 所有題目的 `cat` 都有對應的分類
- [ ] 選擇題 `oe` 長度 = `opts` 長度
- [ ] `a` 索引有效
- [ ] ID 無重複
- [ ] `localStorage` key 已改為唯一值（避免與其他科目衝突）
