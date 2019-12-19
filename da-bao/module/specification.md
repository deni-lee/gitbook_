# 二、模組化規範
## 1.CommonJS
### 1、概述

Node應用由模塊組成，採用CommonJS模塊規範。每個文件就是一個模塊，有自己的作用域。在一個文件裡面定義的變量、函數、類，都是私有的，對其他文件不可見。在服務器端，模塊的加載是運行時同步加載的；在瀏覽器端，模塊需要提前編譯打包處理。
### 2、特點

- 所有代碼都運行在模塊作用域，不會污染全局作用域。
- 模塊可以多次加載，但是只會在第一次加載時運行一次，然後運行結果就被緩存了，以後再加載，就直接讀取緩存結果。要想讓模塊再次運行，必須清除緩存。
- 模塊加載的順序，按照其在代碼中出現的順序。
### 3、基本語法

- 暴露模塊：module.exports = value或exports.xxx = value
- 引入模塊：require(xxx),如果是第三方模塊，xxx為模塊名；如果是自定義模塊，xxx為模塊文件路徑

此處我們有個疑問：CommonJS暴露的模塊到底是什麼? CommonJS規範規定，每個模塊內部，module變量代表當前模塊。這個變量是一個對象，它的exports屬性（即module.exports）是對外的接口。加載某個模塊，其實是加載該模塊的module.exports屬性。
```js
// example.js
var x = 5;
var addX = function (value) {
  return value + x;
};
module.exports.x = x;
module.exports.addX = addX;
```
## 2.AMD

CommonJS規範加載模塊是同步的，也就是說，只有加載完成，才能執行後面的操作。AMD規範則是非同步加載模塊，允許指定回調函數。由於Node.js主要用於服務器編程，模塊文件一般都已經存在於本地硬盤，所以加載起來比較快，不用考慮非同步加載的方式，所以CommonJS規範比較適用。但是，如果是瀏覽器環境，要從服務器端加載模塊，這時就必須採用非同步模式，因此瀏覽器端一般採用AMD規範。此外AMD規範比CommonJS規範在瀏覽器端實現要來著早。

#### AMD規範基本語法

定義暴露模塊 :
```js
//定义没有依赖的模块
define(function(){
   return 模块
})

//定义有依赖的模块
define(['module1', 'module2'], function(m1, m2){
   return 模块
})

引入使用模塊 :
require(['module1', 'module2'], function(m1, m2){
   使用m1/m2
})
```
### 3.CMD

CMD規範專門用於瀏覽器端，模塊的加載是異步的，模塊使用時才會加載執行。CMD規範整合了CommonJS和AMD規範的特點。在Sea.js 中，所有JavaScript 模塊都遵循CMD模塊定義規範。

#### CMD規範基本語法

定義暴露模塊：
```js
//定义没有依赖的模块
define(function(require, exports, module){
  exports.xxx = value
  module.exports = value
})

//定义有依赖的模块
define(function(require, exports, module){
  //引入依赖模块(同步)
  var module2 = require('./module2')
  //引入依赖模块(异步)
    require.async('./module3', function (m3) {
    })
  //暴露模块
  exports.xxx = value
})

引入使用模塊：
define(function (require) {
  var m1 = require('./module1')
  var m4 = require('./module4')
  m1.show()
  m4.show()
})
```
### 4.ES6模塊化

ES6 模塊的設計思想是盡量的靜態化，使得編譯時就能確定模塊的依賴關係，以及輸入和輸出的變量。CommonJS 和AMD 模塊，都只能在運行時確定這些東西。比如，CommonJS 模塊就是對象，輸入時必須查找對象屬性。

#### ES6模塊化語法

export命令用於規定模塊的對外接口，import命令用於輸入其他模塊提供的功能。
```js
/** 定义模块 math.js **/
var basicNum = 0;
var add = function (a, b) {
    return a + b;
};
export { basicNum, add };
/** 引用模块 **/
import { basicNum, add } from './math';
function test(ele) {
    ele.textContent = add(99 + basicNum);
}
```
如上例所示，使用import命令的時候，用戶需要知道所要加載的變量名或函數名，否則無法加載。為了給用戶提供方便，讓他們不用閱讀文檔就能加載模塊，就要用到export default命令，為模塊指定默認輸出。
```js
// export-default.js
export default function () {
  console.log('foo');
}

// import-default.js
import customName from './export-default';
customName(); // 'foo'
```
模塊默認輸出, 其他模塊加載該模塊時，import命令可以為該匿名函數指定任意名字。
