This is an interactive weather website built with Vue.js. Users can query weather information in various parts of Taiwan in two ways.

Hover over the map: Move your mouse over a county or city on the map to display real-time weather information for that area.
Drop-down menu: Select a county or city from the menu, and the website will instantly update the weather conditions for the selected area.

/
├── public/                 # 靜態檔案，例如 index.html
├── src/
│   ├── assets/             # 圖片、字體等靜態資源
│   ├── components/         # 可重用的 Vue 元件
│   │   ├── Map.vue         # 台灣地圖 SVG 顯示與互動邏輯
│   ├── App.vue             # 主要應用程式元件
│   └── main.js             # 應用程式進入點
└── package.json            # 專案依賴與腳本
