# plugin(插件)

loader 用於轉換某些類型的模塊，而插件則可以用於執行範圍更廣的任務。包括：打包優化，資源管理，注入環境變量。

## 用法 

由於插件可攜帶參數/選項，必須在webpack配置中，向plugins屬性替換new實例。
根據你使用webpack的需要，這裡有多種方式使用插件。

## 剖析 

webpack 插件是一個具有apply方法的JavaScript對象。apply方法會被webpack編譯器調用，並且編譯器對象可以在整個編譯生命週期訪問。

```js
ConsoleLogOnBuildWebpackPlugin.js
const pluginName = 'ConsoleLogOnBuildWebpackPlugin';
class ConsoleLogOnBuildWebpackPlugin {
  apply(compiler) {
    compiler.hooks.run.tap(pluginName, compilation => {
      console.log('webpack 构建过程开始！');
    });
  }
}
```
編譯器掛鉤的輕按方法的第一個參數，應該是駝峰式命名的插件名稱。建議使用一個常量，殺死它可以在所有掛鉤中關聯。

## 配置 

```js
//webpack.config.js
const HtmlWebpackPlugin = require('html-webpack-plugin'); //通过 npm 安装
const webpack = require('webpack'); //访问内置的插件
const path = require('path');
 
module.exports = {
  entry: './path/to/my/entry/file.js',
  output: {
    filename: 'my-first-webpack.bundle.js',
    path: path.resolve(__dirname, 'dist')
  },
  module: {
    rules: [
      {
        test: /\.(js|jsx)$/,
        use: 'babel-loader'
      }
    ]
  },
  plugins: [
    new webpack.ProgressPlugin(),
    new HtmlWebpackPlugin({template: './src/index.html'})
  ]
};
```
