# sass-loader

加載Sass / SCSS文件並將其編譯為CSS

## 安裝
```
$ npm install sass-loader node-sass --save-dev
```

## 入門

sass-loader需要您自己安裝Node Sass或Dart Sass。這使您可以控制所有依賴項的版本，並選擇要使用的Sass實現。

將sass-loader與css-loader和style-loader鏈接起來，以立即將所有樣式應用於DOM或mini-css-extract-plugin，以將其提取到單獨的文件中。

然後將加載程序添加到您的webpack配置中。例如：

file.js
```js
import style from './style.scss';
```

file.scss
```css
$body-color: red;
 
body {
  color: $body-color;
}
```

webpack.config.js
```js
module.exports = {
  module: {
    rules: [
      {
        test: /\.s[ac]ss$/i,
        use: [
          // Creates `style` nodes from JS strings
          'style-loader',
          // Translates CSS into CommonJS
          'css-loader',
          // Compiles Sass to CSS
          'sass-loader',
        ],
      },
    ],
  },
};
```

## 參考文獻
https://github.com/webpack-contrib/sass-loader

https://medium.com/@cos214159/webpack-%E7%AD%86%E8%A8%98%E6%95%B4%E7%90%86-%E4%B9%9D-sass-loader-%E5%92%8C-autoprefix-1305ffec77f7