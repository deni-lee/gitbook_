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
菜鳥教程官網地址：www . runoob . com
 文件讀取實例
 ```
創建file.js 文件, 代碼如下：
```js
var fs = require （“ fs” ）; 

//異步讀取
fs . readFile ( 'input.txt' , function ( err , data ) { if ( err ) { return console . error ( err ); } 
   console . log ( "異步讀取: " + data . toString ()); });   
     
       
    


//同步讀取var data = fs . readFileSync ( 'input.txt' ); 
console . log ( "同步讀取: " + data . toString ());
 

console . log ( "程序執行完畢。" );
```
以上代碼執行結果如下：
```
$ node file . js 
 同步讀取: 菜鳥教程官網地址：www . runoob . com
 文件讀取實例 

程序執行完畢。異步讀取: 菜鳥教程官網地址：www . runoob . com
 文件讀取實例
 ```

 ## 參考文獻
 https://ithelp.ithome.com.tw/articles/10185422

 https://www.runoob.com/nodejs/nodejs-fs.html  fs & API

 https://github.com/jprichardson/node-fs-extra  fs-extra官方github & API