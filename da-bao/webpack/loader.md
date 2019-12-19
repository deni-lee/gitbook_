# Loader

## 什麼是Loader ？

在擼一個loader前，我們需要先知道它到底是什麼。本質上來說，loader就是一個node模塊，這很符合webpack中「萬物皆模塊」的思路。既然是node模塊，那就一定會導出點什麼。在webpack的定義中，loader導出一個函數，loader會在轉換源模塊（resource）的時候調用該函數。在這個函數內部，我們可以通過傳入this上下文給Loader API來使用它們。回顧一下頭圖左邊的那些模塊，他們就是所謂的源模塊，會被loader轉化為右邊的通用文件，因此我們也可以概括一下loader的功能：<mark>把源模塊轉換成通用模塊。</mark>

loader用於對模塊的源代碼進行轉換。loader可以使你在import或"加載"模塊時預處理文件。因此，loader類似於其他構建工具中“任務(task)”，並提供了處理前端構建步驟的強大方法。loader可以將文件從不同的語言（如TypeScript）轉換為JavaScript或將內聯圖像轉換為data URL。loader甚至允許你直接在JavaScript模塊中importCSS文件！

## 範例

EX: 

你可以使用loader 告訴webpack 加載CSS 文件，或者將TypeScript 轉為JavaScript。為此，首先安裝相對應的loader：

```
npm install --save-dev css-loader
npm install --save-dev ts-loader
``` 

然後指示webpack對每個.css使用css-loader，以及對所有.ts文件使用ts-loader：

```
//webpack.config.js
module.exports = {
  module: {
    rules: [
      { test: /\.css$/, use: 'css-loader' },
      { test: /\.ts$/, use: 'ts-loader' }
    ]
  }
};
```

在你的應用程序中，有三種使用loader 的方式：

- 配置（推薦）：在webpack.config.js文件中指定loader。
- 內聯：在每個import語句中顯式指定loader。
- CLI：在shell命令中指定它們。

## loader 特性 
  
- loader 支持鍊式傳遞。鏈中的每個loader 會將轉換應用在已處理過的資源上。一組鍊式的loader 將按照相反的順序執行。鏈中的第一個loader 將其結果（也就是應用過轉換後的資源）傳遞給下一個
- loader，依此類推。最後，鏈中的最後一個loader，返回webpack 期望JavaScript。
- loader 可以是同步的，也可以是異步的。
- loader 運行在Node.js 中，並且能夠執行任何Node.js 能做到的操作。
- loader可以通過options對象配置（仍然支持使用query參數來設置選項，但是這種方式已被廢棄）。
- 除了常見的通過package.json的main來將一個npm模塊導出為loader，還可以在module.rules中使用loader字段直接引用一個模塊。
- 插件(plugin)可以為loader 帶來更多特性。
- loader 能夠產生額外的任意文件。

通過（loader）預處理函數，loader為JavaScript生態系統提供了更多能力。用戶現在可以更加靈活地引入細粒度邏輯，例如：壓縮、打包、語言翻譯和更多其他特性。
