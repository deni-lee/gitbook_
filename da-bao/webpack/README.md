# webpack

## Webpack是什麼

webpack是個模組打包工具。你可以使用單獨的task runner，同時讓webpack來處理打包，當然webpack已經有外掛作為task runner。 有時這些外掛被用來i執行在webpack外部完成的任務，如清理構建的目錄或者部署本次構建。
webpack在使用React的時候很常用，由於Hot Module Replacement(HMR)的幫助，可以在其他環境使用，如Ruby on Rails。
儘管它的名字是web+pack，但是webpack不僅可以使用在web端。

## 為什麼要 Webpack？
網頁寫久了，難免你會使用到一些需要編譯的語法來加速開發時間。像是 scss 啊、less啊、coffee啊、react啊、vue啊，甚至是 ES6。但瀏覽器並沒有支援這些語法。所以我們需要編譯器幫我們把這些語法做編譯轉為原生語法。

你可以：

- 將你的 js 檔案 Bundle 變成單一的檔案
- 在你的前端程式碼中使用 npm packages
- 撰寫 JavaScript ES6 或 ES7（需要透過 babel 來幫助）
- Minify 或優化程式碼
將 LESS 或 SCSS 轉換成 CSS
- 使用 HMR（Hot Module Replacement）
- 包含任何類型的檔案到你的 JavaScript
- 更多進階的東西

## 為什麼我需要這些功能？
- Bundle JS 檔案 - 讓你可以撰寫模組化的 JavaScript，但是你不需要 include 每個 JavaScript　<code>&lt;script&gt; </code>的檔案（如果你需要多個 JavaScript 檔案可以透過設定來完成）。
- 在你的前端程式碼中使用 npm packages - npm 在 internet 上是一個大型的 open source 生態系統。可以儲存或發佈你的程式碼，你可以到 npm 看一看，可能包含你想要的前端套件。
- ES6 和 ES7 - 加入一些 JavaScript 的新功能，讓撰寫程式碼可以更容易而且更強大，請看這裡的介紹。
- Minify 或優化程式碼 - 減少你的檔案大小，好處包括像是更快的將頁面載入。
將 LESS 或 SCSS 轉換成 CSS - 使用更好的方式來撰寫 CSS， 如果你不熟悉的話，這裡有一些介紹。
- 使用 HMR - 增加開發速度。每當你儲存程式碼的時候，它可以注入到網頁，而不需將網頁刷新。如果當編輯你的程式碼，你需要維護頁面的狀態，這是非常方便的。
- 包含任何類型的檔案到你的 JavaScript - 減少對其他 build 工具的需要，讓你可以透過程式的方式修改或使用這些檔案。
