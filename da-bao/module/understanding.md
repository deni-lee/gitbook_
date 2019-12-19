# 一、模組化的理解


## 1.什麼是模組?
將一個複雜的程序依據一定的規則(規範)封裝成幾個塊(文件), 並進行組合在一起
塊的內部數據與實現是私有的, 只是向外部暴露一些接口(方法)與外部其它模組通信

## 2.模組化的進化過程
### 全局function模式: 將不同的功能封裝成不同的全局函數

編碼: 將不同的功能封裝成不同的全局函數

問題: 污染全局命名空間, 容易引起命名衝突或數據不安全，而且模組成員之間看不出直接關係

```js
function m1(){
  //...
}
function m2(){
  //...
}
```
### namespace模式: 簡單對象封裝
作用: 減少了全局變量，解決命名衝突 

問題: 數據不安全(外部可以直接修改模組內部的數據)
```js
let myModule = {
  data: 'www.test.com',
  foo() {
    console.log(`foo() ${this.data}`)
  },
  bar() {
    console.log(`bar() ${this.data}`)
  }
}
myModule.data = 'other data' //能直接修改模块内部的数据
myModule.foo() // foo() other data
```
這樣的寫法會暴露所有模組成員，內部狀態可以被外部改寫。

### IIFE模式：匿名函數自調用(閉包)
作用: 數據是私有的, 外部只能通過暴露的方法操作

編碼: 將數據和行為封裝到一個函數內部, 通過給window添加屬性來向外暴露接口

問題: 如果當前這個模組依賴另一個模組怎麼辦?
```js
// index.html文件
<script type="text/javascript" src="module.js"></script>
<script type="text/javascript">
    myModule.foo()
    myModule.bar()
    console.log(myModule.data) //undefined 不能访问模块内部数据
    myModule.data = 'xxxx' //不是修改的模块内部的data
    myModule.foo() //没有改变
</script>
```

```js
// module.js文件
(function(window) {
  let data = 'www.test.com'
  //操作数据的函数
  function foo() {
    //用于暴露有函数
    console.log(`foo() ${data}`)
  }
  function bar() {
    //用于暴露有函数
    console.log(`bar() ${data}`)
    otherFun() //内部调用
  }
  function otherFun() {
    //内部私有的函数
    console.log('otherFun()')
  }
  //暴露行为
  window.myModule = { foo, bar } //ES6写法
})(window)
```
最後得到的結果：
```
foo() www.test.com
bar() www.test.com
otherFun()
undefined 
foo() www.test.com
```
### IIFE模式增強: 引入依賴
這就是現代模組實現的基石
```js
// module.js文件
(function(window, $) {
  let data = 'www.baidu.com'
  //操作数据的函数
  function foo() {
    //用于暴露有函数
    console.log(`foo() ${data}`)
    $('body').css('background', 'red')
  }
  function bar() {
    //用于暴露有函数
    console.log(`bar() ${data}`)
    otherFun() //内部调用
  }
  function otherFun() {
    //内部私有的函数
    console.log('otherFun()')
  }
  //暴露行为
  window.myModule = { foo, bar }
})(window, jQuery)
```
```js
// index.html文件
  <!-- 引入的js必须有一定顺序 -->
  <script type="text/javascript" src="jquery-1.10.1.js"></script>
  <script type="text/javascript" src="module.js"></script>
  <script type="text/javascript">
    myModule.foo()
  </script>
```
上例子通過jquery方法將頁面的背景顏色改成紅色，所以必須先引入jQuery庫，就把這個庫當作參數傳入。這樣做除了保證模塊的獨立性，還使得模塊之間的依賴關係變得明顯。

## 3.模組化的好處

- 避免命名衝突(減少命名空間污染)
- 更好的分離, 按需加載
- 更高複用性
- 高可維護性


## 4.引入多個<code>&lt;script&gt;</code>後出現問題

- 請求過多

首先我們要依賴多個模組，那樣就會發送多個請求，導致請求過多
- 依賴模糊

我們不知道他們的具體依賴關係是什麼，也就是說很容易因為不了解他們之間的依賴關係導致加載先後順序出錯。
- 難以維護

以上兩種原因就導致了很難維護，很可能出現牽一發而動全身的情況導致項目出現嚴重的問題。模組化固然有多個好處，然而一個頁面需要引入多個js文件，就會出現以上這些問題。而這些問題可以通過模組化規範來解決，下面介紹開發中最流行的commonjs, AMD, ES6, CMD規範。


