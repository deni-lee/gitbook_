# 入口(entry) 
入口起點(entry point)指示webpack應該使用哪個模塊，來作為構建其內部依賴圖(dependency graph)的開始。進入入口起點後，webpack會找出有哪些模塊和庫是入口起點（直接和間接）依賴的。
 
### 單個入口（簡寫）語法 

用法：entry: string|Array<string>

```js
//webpack.config.js
module.exports = {
  entry: './path/to/my/entry/file.js'
};
entry 屬性的單個入口語法，是下面的簡寫：
webpack.config.js
module.exports = {
  entry: {
    main: './path/to/my/entry/file.js'
  }
};
```
當你正在尋找為「只有一個入口起點的應用程序或工具（即library）」快速設置webpack 配置的時候，這會是個很不錯的選擇。然而，使用此語法在擴展配置時有失靈活性。

### 對象語法 

用法：entry: {[entryChunkName: string]: string|Array<string>}
```js
webpack.config.js
module.exports = {
  entry: {
    app: './src/app.js',
    adminApp: './src/adminApp.js'
  }
  };
```
對象語法會比較繁瑣。然而，這是應用程序中定義入口的最可擴展的方式。

### 多頁面應用程序 
```js
//webpack.config.js
module.exports = {
  entry: {
    pageOne: './src/pageOne/index.js',
    pageTwo: './src/pageTwo/index.js',
    pageThree: './src/pageThree/index.js'
  }
};
```
這是什麼？我們告訴webpack需要三個獨立分離的依賴圖（如上面的示例）。
為什麼？在多頁面應用程序中，服務器會傳輸一個新的HTML文檔給你的客戶端。頁面重新加載此新文檔，並且資源被重新下載。然而，這給了我們特殊的機會去做很多事：

- 使用optimization.splitChunks為頁面間共享的應用程序代碼創建bundle。由於入口起點增多，多頁應用能夠復用入口起點之間的大量代碼/模塊，從而可以極大地從這些技術中受益。
