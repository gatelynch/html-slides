---
name: html-slides
description: 生成、改版與整理單檔 HTML 簡報。當使用者要做簡報、slide deck、HTML 簡報、講者備註、教學活動簡報、或準備發布到 GitHub Pages 時使用。本 skill 以 HTML 為主要輸出。
---

# HTML 簡報

製作零建置、可直接在瀏覽器開啟的單檔 HTML 簡報。主要輸出是 `.html`；CSS 與 JavaScript 內嵌於同一檔案，圖片、截圖、影音等大型資產放在相鄰的 `assets/` 目錄，並使用相對路徑。

## 使用原則

- 以 HTML 簡報為唯一主要輸出；不要改走 Marp、PowerPoint 或 Obsidian Markdown，除非使用者明確要求。
- 每頁使用 `<section class="slide">`，一頁只承載一個核心訊息；頁面不可依賴內部捲動，內容太多就拆頁。
- 預設風格是 **Clean**。可選風格固定為六種：Clean、Workshop、Notebook、Story、Lab、Dark。
- 版型固定從 22 種中選擇：12 種通用版型加 10 種教學版型。不要臨時發明一套難以維護的頁型命名。
- 所有風格都必須遵守同一組 CSS token：`--bg-primary`、`--text-primary`、`--text-secondary`、`--accent`、`--accent-dim`、`--surface`、`--border`、`--on-accent`、`--font-title`、`--font-body`。
- 動畫、進度條、鍵盤導覽是建議配置；可依正式簡報、講義、現場教學、無障礙或輸出場合省略。若加入動畫，必須低調、可讀、支援 `prefers-reduced-motion`。
- 既有簡報改版時，先理解原本結構與風格，再做局部調整；不要順手重寫無關頁面。

## 先問清楚

開始生成整份簡報前，先確認這些資訊。若使用者已經提供答案，就不要重複詢問。

1. 簡報目的與受眾是誰？
2. 內容目前是完整素材、粗略大綱，還是只有主題？
3. 預計講多久、需要幾頁左右？
4. 想要哪一種風格？若沒有偏好，使用 Clean。
5. 是否需要講者備註？
6. 是否有圖片、截圖或其他資產要放進簡報？
7. 是否需要之後發布到 GitHub Pages？

若是教學簡報，還要特別確認：

- 現場是講述、討論、實作，還是混合？
- 學習者要先嘗試，還是先看範例？
- 每個活動的輸入、任務、產出、時間限制與討論問題是什麼？

## 工作流程

1. **規劃簡報骨架**  
   先提出頁面順序、每頁功能、預計使用的版型與風格，不要一開始就把所有內容塞成完整 HTML。教學簡報尤其要先安排「嘗試、揭示、比較、修正」的節奏。

2. **選定風格與版型**  
   從 `references/style-system.md` 選一種風格，從 `references/deck-patterns.md` 與 `references/teaching-patterns.md` 選頁型。相鄰頁避免連續使用同一種版型。

3. **生成或改版 HTML**  
   必要時從 `assets/templates/base-deck.html` 開始。保留單檔 HTML 架構，CSS token 放在 `:root` 或風格 class 裡，頁面使用 `<section class="slide">`。

4. **處理視覺與資產**  
   圖片使用相對路徑。若使用者提供本機圖片，將圖片放到簡報相鄰的 `assets/` 子資料夾，避免 HTML 依賴本機絕對路徑。

5. **加入講者備註**  
   若需要備註，使用 `data-note` 或等價結構保存每頁提示。顯示方式由該份簡報需求決定；不要把手機版備註模式當作通用預設。

6. **人工瀏覽器 QA**  
   完成後用瀏覽器逐頁檢查。檢查標準見 `references/qa-checklist.md`。

7. **交付**  
   回報檔案位置、檢查結果、如何開啟。若使用者要求發布，再參考 `references/github-pages.md`。

## 需要時讀取的參考

- `references/style-system.md`：六種固定風格、CSS token、字級、密度、動畫與視覺規格。
- `references/deck-patterns.md`：22 種頁型（12 通用 + 10 教學）的 HTML 結構速查、導覽與講者備註；教學頁型的設計細節見 `teaching-patterns.md`。
- `references/teaching-patterns.md`：10 種教學頁型與現場活動節奏。
- `references/qa-checklist.md`：人工瀏覽器 QA 檢查清單。
- `references/github-pages.md`：將 HTML 簡報整理成 GitHub Pages 可發布狀態。
- `assets/templates/base-deck.html`：可直接複製改寫的單檔 HTML 範本。

## 不要做的事

- 不要把簡報寫成需要建置工具或框架才能開啟的專案。
- 不要只產出大量條列，忽略活動、圖像、對比、流程與範例。
- 不要把動畫做成主角；動畫只是引導注意力，且可依場合省略。
- 不要硬塞內容導致頁面需要捲動。
- 不要在沒有檢查瀏覽器畫面的情況下宣稱排版完成。
