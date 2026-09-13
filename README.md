# 幸運蔬齋

Vue 3 + Vite 響應式品牌網站。

## 本機開發

```sh
npm install
npm run dev
```

## 正式版建置

```sh
npm run build
npm run preview
```

部署 `dist` 資料夾至靜態網站服務即可。建議使用 Node.js 22.12 以上。

網站包括手機導覽、餐點分類切換、品牌故事及 Google 地圖連結。餐點插畫為 SVG 示意；尚未提供的價格、電話、地址和營業時間未擅自填寫。上線前可於 `src/App.vue` 更新店家確認的文案與餐點資料，並以實際餐點照片替換插畫。字型使用 Google Fonts，無網路時會回退系統字型。
