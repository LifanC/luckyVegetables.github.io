# 幸運蔬齋

幸運蔬齋的響應式品牌網站，以 Vue 3 + Vite 建置，介紹招牌餐點、品牌故事與來店資訊。

## 網站功能

- 響應式版面與手機版導覽選單。
- 餐點分類切換，展示素食水煎包、素食麵線、素食南部粽與豆漿，並顯示各分類的品項數量。
- 餐點照片、店面照片與品牌故事。
- 嵌入式 Google 地圖與開啟店家地圖的連結。
- 頁內區塊導覽與回到頁首功能。

## 開發環境

- Node.js：建議使用 22.12 以上的 22.x 版本。
- npm：使用專案內的 `package-lock.json` 安裝相同版本的相依套件。

主要技術為 Vue 3、Vite 7 與 `@vitejs/plugin-vue`，樣式使用原生 CSS。

## 本機開發

```sh
npm ci
npm run dev
```

開啟終端機顯示的本機網址。由於目前設定了 `base`，開發路徑包含 `/luckyVegetables.github.io/`。

## 正式版建置

```sh
npm run build
npm run preview
```

建置結果輸出至 `dist/`，可部署到靜態網站服務。`npm run preview` 用於本機預覽建置成果。

## 專案結構

```text
├── .github/workflows/deploy.yml  # GitHub Pages 自動部署
├── img/                         # 餐點、店面照片、品牌標誌與 favicon
├── src/
│   ├── components/BunArt.vue    # 餐點圖片與替代文字對應
│   ├── App.vue                  # 頁面內容、餐點資料與互動邏輯
│   ├── main.js                  # Vue 應用程式入口
│   └── style.css                # 全站樣式與響應式版面
├── index.html                   # 網頁標題、描述與 favicon 設定
├── package.json                 # 相依套件與 npm 指令
└── vite.config.js               # Vite 與部署路徑設定
```

## 內容維護

| 項目 | 修改位置 |
| --- | --- |
| 餐點名稱、分類、介紹與標籤 | `src/App.vue` 的 `foods` 陣列；分類選項會依資料自動產生 |
| 餐點照片與替代文字 | `src/components/BunArt.vue`；目前使用 `img/a.jpg`（水煎包）、`b.jpg`（麵線）、`c.jpg`（南部粽）、`d.jpg`（豆漿） |
| 店面照片與品牌標誌 | `img/head.jpg` 與 `img/logo.svg` |
| 品牌文案與來店資訊 | `src/App.vue` |
| 店家地圖 | 同步更新 `src/App.vue` 的 `maps` 連結與地圖 `iframe` 的 `src` |
| 色彩、字型與版面 | `src/style.css` |
| 網頁標題與搜尋描述 | `index.html` 的 `<title>` 與 description 中繼標籤 |

新增餐點時，請讓 `foods` 中的 `type` 對應到 `BunArt.vue` 的 `images` 設定，並匯入對應照片。

網站未列出價格、電話、完整地址與營業時間；餐點價格及供應情況以店家現場資訊為準，地址與營業時間引導訪客查看 Google 地圖。更新時請使用店家確認的資料。

字型透過 Google Fonts 載入 Noto Sans TC 與 Noto Serif TC；無法載入時會使用備援字型。嵌入式地圖需要網路連線。

## GitHub Pages 部署

專案已提供 `.github/workflows/deploy.yml`。推送至 `master` 分支時，工作流程會使用 Node.js 20，執行 `npm ci` 與 `npm run build`，再將 `dist/` 部署至 GitHub Pages。儲存庫的 Pages 建置來源需設定為 GitHub Actions。

`vite.config.js` 目前的部署基底路徑為：

```js
base: '/luckyVegetables.github.io/'
```

部署前請確認此路徑與實際網站位置一致。若網站放在網域根目錄（例如 `<帳號>.github.io` 的使用者網站或自訂網域根目錄），請改為 `/`；若放在專案子路徑，則使用 `/<儲存庫名稱>/`。修改後需重新建置。
