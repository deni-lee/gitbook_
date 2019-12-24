# 輸出 output

output屬性告訴webpack在哪裡輸出它所創建的bundle，以及如何命名這些文件。主要輸出文件的默認值是./dist/main.js，其他生成文件默認放置在./dist文件夾中。

## 用法（用法）

在webpack中配置output屬性的最低要求是，將它的值設置為一個對象，包括以下屬性： filename 用於輸出文件的文件名。

```javascript
//webpack.config.js
module.exports = {
  output: {
    filename: 'bundle.js',
  }
};
```

## 多個入口起點

如果配置創建了多個單獨的“ chunk”（例如，使用多個入口起點或使用像CommonsChunkPlugin這樣的插件），則應該使用佔位符（替代）來確保每個文件具有唯一的名稱。

```javascript
module.exports = {
  entry: {
    app: './src/app.js',
    search: './src/search.js'
  },
  output: {
    filename: '[name].js',
    path: __dirname + '/dist'
  }
};
```

