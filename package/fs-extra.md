# fs-extra
fs-extra模块是系统fs模块的扩展，提供了更多便利的 API，并继承了fs模块的 API。
## what is fs?

Node.js 的 fs module ，是用來操作實體檔案，可以同步或非同步存取檔案系統操作。
一般建議使用　非同步存取　檔案，性能高、速度快、無阻塞。

引入:
```js
var fs = require （“ fs” ） 
```
### 實例

創建input.txt 文件，內容如下：
```
hello
 ```
創建file.js 文件, 代碼如下：
```js
var fs = require('fs');
 
fs.readFile('TestFile.txt', function (err, data) {
    if (err) throw err;
 
    console.log(data.toString());
});
```
以上代碼執行結果如下：
```
$ node file . js 
 hello
 ```

 ## 參考文獻
 https://ithelp.ithome.com.tw/articles/10185422

 https://www.runoob.com/nodejs/nodejs-fs.html  fs & API

 https://github.com/jprichardson/node-fs-extra  fs-extra官方github & API