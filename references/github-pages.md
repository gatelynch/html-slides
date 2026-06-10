# GitHub Pages 發布整理

只有在使用者明確要求發布時，才處理 GitHub Pages。生成簡報本身不需要自動發布。

## 檔案整理

建議結構：

```text
repo/
  index.html
  assets/
    image-1.jpg
    image-2.png
```

HTML 內的圖片路徑必須使用相對路徑：

```html
<img src="assets/image-1.jpg" alt="課堂活動照片">
```

不要使用本機絕對路徑，例如 `/Volumes/...`，因為發布後會失效。

## 發布前檢查

- `index.html` 可以直接用瀏覽器開啟。
- 所有圖片都在 repo 內。
- HTML 沒有依賴本機絕對路徑。
- 檔名避免空白與特殊符號，優先使用小寫 kebab-case。
- 手動用瀏覽器檢查發布後網址。

## 回報內容

發布完成後，回報：

- GitHub repo 名稱。
- GitHub Pages 網址。
- 是否已檢查圖片與導覽正常。
