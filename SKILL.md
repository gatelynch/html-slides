---
name: html-slides
description: 生成、改版與整理單檔 HTML 簡報。當使用者要做簡報、slide deck、HTML 簡報、講者備註、教學活動簡報、或準備發布到 GitHub Pages 時使用。本 skill 以 HTML 為主要輸出。
---

# HTML 簡報

製作零建置、可直接在瀏覽器開啟的單檔 HTML 簡報。主要輸出是 `.html`；CSS 與 JavaScript 內嵌於同一檔案，圖片、截圖、影音等大型資產放在相鄰的 `assets/` 目錄，並使用相對路徑。

## 使用原則

- 以 HTML 簡報為唯一主要輸出；不要改走 Marp、PowerPoint 或 Obsidian Markdown，除非使用者明確要求。
- 預設先產出草案 markdown（逐頁重點），與使用者確認後再生成 HTML；除非使用者明確要求直接出 HTML。草案只是中間產物，不是另一種交付格式。
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

1. **先寫草案 markdown，不要直接生成 HTML**  
   規劃好頁面順序與骨架後，先輸出一份草案 `.md`：每張投影片一個區塊，簡述版型、標題與重點，必要時加講者備註與所需圖片。檔頭記錄目的、受眾、風格、頁數與時長。風格從 `references/style-system.md` 選，版型從 `references/deck-patterns.md` 與 `references/teaching-patterns.md` 選，相鄰頁避免連用同一種版型。格式與範例見 `references/outline-format.md`。

2. **與使用者確認草案**  
   把草案交給使用者檢視：增刪頁面、調整順序與版型、補齊重點。教學簡報要在這個階段就把「嘗試、揭示、比較、修正」的節奏排好。草案確認後才進入 HTML；除非使用者明確要求直接出 HTML，否則不要跳過這一步。

3. **依草案生成 HTML**  
   草案確認後，必要時從 `assets/templates/base-deck.html` 開始，把每個草案區塊轉成 `<section class="slide">`。保留單檔 HTML 架構，CSS token 放在 `:root` 或風格 class 裡。

4. **處理視覺與資產**  
   圖片使用相對路徑。若使用者提供本機圖片，將圖片放到簡報相鄰的 `assets/` 子資料夾，避免 HTML 依賴本機絕對路徑。

5. **加入講者備註**  
   若需要備註，使用 `data-note` 或等價結構保存每頁提示。顯示方式由該份簡報需求決定；不要把手機版備註模式當作通用預設。

6. **人工瀏覽器 QA**  
   完成後用瀏覽器逐頁檢查。檢查標準見 `references/qa-checklist.md`。

7. **自我驗證：逐頁交代並對照成功標準**  
   宣稱完成前，主動向使用者攤開下面兩份東西，讓使用者能快速核對、抓出問題，而不是只說一句「做好了」：
   - **逐頁清單（markdown）**：列出每一頁的版型、標題與一句核心訊息，據此確認真的一頁一重點、相鄰頁沒有重複或漏接。
   - **成功標準自評**：逐條對照本份簡報的成功標準（一頁一畫面、不依賴捲動、風格與版型都在固定集合內、CSS token 一致、視覺焦點明確、符合受眾與時間），說明哪裡符合；不符合或沒把握的，直接點出並說明後續處理，不要含糊帶過。  
   這一步的重點是用「把判斷講出來」逼自己對齊標準，不是事後補一段漂亮的說明。

8. **交付**  
   回報草案與 HTML 的檔案位置、檢查結果、如何開啟。若使用者要求發布，再參考 `references/github-pages.md`。

## 需要時讀取的參考

- `references/outline-format.md`：草案 markdown 的格式與範例（生成 HTML 前的逐頁重點）。
- `references/style-system.md`：六種固定風格、CSS token、字級、密度、動畫與視覺規格。
- `references/deck-patterns.md`：22 種頁型（12 通用 + 10 教學）的 HTML 結構速查、導覽與講者備註；教學頁型的設計細節見 `teaching-patterns.md`。
- `references/teaching-patterns.md`：10 種教學頁型與現場活動節奏。
- `references/qa-checklist.md`：人工瀏覽器 QA 檢查清單。
- `references/github-pages.md`：將 HTML 簡報整理成 GitHub Pages 可發布狀態。
- `assets/templates/base-deck.html`：可直接複製改寫的單檔 HTML 範本。

## 不要做的事

- 不要跳過草案直接生成整份 HTML，除非使用者明確要求。
- 不要把簡報寫成需要建置工具或框架才能開啟的專案。
- 不要只產出大量條列，忽略活動、圖像、對比、流程與範例。
- 不要把動畫做成主角；動畫只是引導注意力，且可依場合省略。
- 不要硬塞內容導致頁面需要捲動。
- 不要在沒有檢查瀏覽器畫面的情況下宣稱排版完成。
- 不要在沒有逐頁交代核心訊息、也沒有對照成功標準的情況下宣稱完成。
