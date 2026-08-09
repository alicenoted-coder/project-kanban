# project-kanban

佈告欄 —— 直式專案看板，為 e-ink 螢幕設計（純黑白、無灰階、無動畫）。

## 頁面

`index.html` 是完整的單檔應用，沒有相依套件，直接開就能用。

三個分頁，閒置 90 秒會自動輪播；操作後暫停 3 分鐘：

- **一覽** —— 依欄位分組列出所有專案、下一步、預估時間
- **看板** —— 單欄檢視，可切欄、改下一步、調時間、前後搬動卡片
- **心錨** —— 每日一句

「我現在有 15 分／30 分／1 小時」的篩選會跨欄撈出做得完的下一步。

## 資料

存在瀏覽器本機：`poke-board-v3`（若環境提供 `window.storage` 則優先用它）。
首次啟動會依序嘗試沿用 `poke-board-v2`、`poke-board-v1`，都沒有的話再從
`project-kanban-v1` 匯入一次。

## 部署

網址：<https://alicenoted-coder.github.io/project-kanban/>

站台從 `gh-pages` 分支發佈。推到 `main` 之後，`.github/workflows/publish.yml`
會把 `main` 原樣鏡像到 `gh-pages`，GitHub 收到那一推就重建站台。沒有建置步驟 ——
站台就是根目錄的 `index.html`，`.nojekyll` 用來關掉 Jekyll 處理。

`gh-pages` 是機器維護的鏡像，不要直接在上面改東西，下一次推 `main` 就會被蓋掉。

沒有用 `actions/deploy-pages`，因為那需要把 Pages 來源改成 GitHub Actions，
而建立或變更 Pages 設定的 API 不開放給 workflow 的 `GITHUB_TOKEN`
（`Resource not accessible by integration`）。
