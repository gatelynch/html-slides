# html-slides

一個 [Claude Code](https://claude.com/claude-code) skill，用來**生成、改版與整理單檔 HTML 簡報**。

當你要做簡報、slide deck、教學活動簡報、講者備註，或準備發布到 GitHub Pages 時觸發。輸出以零建置、可直接在瀏覽器開啟的單檔 `.html` 為主——CSS 與 JavaScript 內嵌於同一檔案，圖片等大型資產放相鄰的 `assets/` 目錄並用相對路徑。

## 特色

- **6 種風格**：Clean（預設）、Workshop、Notebook、Story、Lab、Dark，共用同一組 CSS token。
- **22 種版型**：12 種通用 + 10 種教學版型，避免臨時發明難維護的頁型。
- **教學導向**：內建教學活動版型（輸入／任務／產出／時間／討論），適合工作坊與課堂。
- **可發布**：支援輸出到 GitHub Pages。
- **無障礙友善**：動畫低調、可讀，支援 `prefers-reduced-motion`。

## 內容結構

```
html-slides/
├── SKILL.md                      # skill 主檔（流程與原則）
├── references/
│   ├── deck-patterns.md          # 通用版型
│   ├── teaching-patterns.md      # 教學版型
│   ├── style-system.md           # 風格與 CSS token
│   ├── github-pages.md           # 發布到 GitHub Pages
│   └── qa-checklist.md           # 交付前檢查清單
└── assets/
    └── templates/
        └── base-deck.html        # 基礎簡報模板
```

## 安裝

把整個資料夾放到 Claude Code 的 skills 目錄：

**個人全域**（所有專案可用）：

```bash
git clone https://github.com/gatelynch/html-slides.git ~/.claude/skills/html-slides
```

**單一專案**：

```bash
git clone https://github.com/gatelynch/html-slides.git <你的專案>/.claude/skills/html-slides
```

裝好後，在 Claude Code 裡提到「做簡報 / HTML 簡報 / slide deck」即會自動觸發。

## 使用

直接告訴 Claude 你的需求即可，例如：

> 幫我做一份介紹班級 AI 規範的教學簡報，Workshop 風格，大約 15 頁，需要講者備註。

Claude 會先確認簡報目的、受眾、頁數與風格，再生成單檔 HTML。
