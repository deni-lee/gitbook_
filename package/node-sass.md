# node-sass

Node-sass是一個庫，提供了Node.js與LibSass（流行的樣式表預處理器Sass的C版本）的綁定。 它使您能夠以驚人的速度通過連接中間件自動將.scss文件本地編譯為css。

## 安裝

```text
npm install node-sass
```

## 用法

```javascript
var sass = require('node-sass');
sass.render({
  file: scss_filename,
  [, options..]
}, function(err, result) { /*...*/ });
// OR
var result = sass.renderSync({
  data: scss_content
  [, options..]
});
```

## 執行

將 index.scss 處理成 index.css

下指令

```text
npm run build-css ./index.scss ./index.css
```

這樣一來，指令就會組成

```text
node-sass index.scss index.css
```

就會依 node-sass 輸入檔 輸出檔 的格式執行。

## 參考文獻

[https://github.com/sass/node-sass](https://github.com/sass/node-sass)

[https://dwatow.github.io/2018/03-12-node-sass](https://dwatow.github.io/2018/03-12-node-sass)

