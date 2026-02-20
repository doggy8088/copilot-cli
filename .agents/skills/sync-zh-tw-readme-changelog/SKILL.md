---
name: sync-zh-tw-readme-changelog
description: '同步並翻譯 README.md 與 changelog.md（繁體中文，zh-tw）。用於 upstream 對齊、增量版本翻譯、只翻新區塊、prepend 到本地 changelog。關鍵字：README 翻譯、CHANGELOG 增量翻譯、zh-tw、術語正規化。'
argument-hint: 'upstream repo（預設 github/copilot-cli）與是否同步 README'
user-invocable: true
---

# 同步 README 與 CHANGELOG（zh-tw）

將 upstream 文件同步到本地，並以繁體中文（台灣用語）輸出。

## 何時使用

- 使用者要求「同步 upstream README」。
- 使用者要求「只翻譯 changelog 新版本，舊內容不重翻」。
- 使用者要求「把新翻譯區塊 prepend 到本地 changelog 最上方」。
- 需要統一採用台灣技術詞彙。

## 輸入參數（可選）

- `upstreamRepo`：預設 `github/copilot-cli`
- `syncReadme`：預設 `true`
- `syncChangelog`：預設 `true`

## 流程

1. 讀取來源與本地檔案
   - 讀取 upstream `README.md`、`changelog.md`。
   - 讀取本地 `README.md`、`changelog.md`。

2. README 條件式更新（若 `syncReadme=true`）
   - 先比較 upstream 與本地 `README.md` 是否有內容差異。
   - 若無差異：不修改本地 `README.md`。
   - 若有差異：將 upstream `README.md` 全文翻譯為繁體中文後覆蓋本地檔案。
   - 翻譯時保持原始 Markdown 結構不變：標題層級、清單、表格、程式碼區塊。
   - 圖片連結、超連結 URL、程式碼片段、命令列內容保持原樣。

3. CHANGELOG 增量翻譯（若 `syncChangelog=true`）
   - 比對 upstream 與本地 `changelog.md`。
   - 以「版本區塊標題」判定新區塊（例如 `##`/`###` 版本標題）。
   - 僅翻譯 upstream 中「本地尚未存在」的新版本區塊。
   - 將翻譯後的新區塊 prepend 到本地 `changelog.md` 上方。
   - 不重新翻譯本地已存在內容。

4. 術語正規化
   - 套用 [繁中術語對照](./references/zh-tw-terms.md)。
   - 優先使用台灣常見技術用語（例如：資料、執行、啟用、支援、伺服器、雲端）。

5. 驗收與輸出
   - README：確認 Markdown 結構、連結 URL、圖片 URL 未被改動。
   - CHANGELOG：確認僅新增缺少版本，且是 prepend。
   - 列出本次新增版本清單與修改檔案摘要。

## 分支邏輯

- 若本地 `changelog.md` 已含所有 upstream 版本：
  - 不修改 `changelog.md`。
  - 回報「無新版本區塊」。

- 若 upstream 與本地 `README.md` 無差異：
   - 不修改 `README.md`。
   - 回報「README 無需更新」。

- 若偵測到檔案前置區塊（例如 YAML frontmatter）：
  - 保留前置區塊於檔首。
  - 將新翻譯版本插入於前置區塊之後。

- 若 upstream 檔案不存在：
  - 中止對應檔案同步並回報缺失項目。
  - 其他可執行項目繼續。

## 完成標準

- `README.md` 僅在 upstream 有變更時更新，更新後與 upstream 對齊且為繁體中文。
- `changelog.md` 僅新增 upstream 新版本翻譯區塊。
- 舊翻譯內容完整保留。
- 術語符合繁中（台灣）慣用法。
