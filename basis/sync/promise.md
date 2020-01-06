# promise

## 意義

Promise，如字面的意思就代表 承諾。

**當你拿到一個 Promise 的時候，代表在未來中這個 Promise 可能會有幾種狀況發生**

- 承諾 被兌現 (fulfilled)

  用 <code>resolve()</code> 來兌現

- 承諾 被打破 (rejected)

  用 <code>reject()</code> 來表示失敗

- 承諾 一直沒有回應 (pending)

  一直沒有回傳

也就是說，承諾代表的不見得是成功。


**而根據這三種結果，我們接下來的動作會有所不同，如果：**

- 承諾被兌現 就 繼續做預定好的下一件事

  使用 <code>.then()</code>

- 承諾被打破 就 根據這個原因去做對應的動作

  使用 <code>.catch()</code>，或是 .then 的第二個參數

- 承諾 一直都沒有回應 就 繼續等下去

## 用法

```js
const myFirstPromise = new Promise((resolve, reject) => {
  resolve(someValue);         // 完成
  reject("failure reason");   // 拒絕
});
```

如果我們需要依序串連執行多個 promise 功能的話，可以透過 .then() 來做到。

EX:
```js
function funcA(){
  return new Promise(function(resolve, reject){
    window.setTimeout(function(){
      console.log('A');
      resolve('A');
    }, (Math.random() + 1) * 1000);
  });
}

function funcB(){
  return new Promise(function(resolve, reject){
    window.setTimeout(function(){
      console.log('B');
      resolve('B');
    }, (Math.random() + 1) * 1000);
  });
}

function funcC(){
  return new Promise(function(resolve, reject){
    window.setTimeout(function(){
      console.log('C');
      resolve('C');
    }, (Math.random() + 1) * 1000);
  });
}
```
最後透過呼叫
```js
funcA().then(funcB).then(funcC);
```
就可以做到等 <code>funcA()</code> 被 「resolve」之後再執行 <code>funcB()</code>，然後 resolve 再執行 <code>funcC()</code> 的順序了。