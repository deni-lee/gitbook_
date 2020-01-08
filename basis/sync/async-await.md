# async/await

在 ES7 裡頭 `async` 的本質是 `promise` 的語法糖 ，只要 function 標記為 `async`，就表示裡頭可以撰寫 `await` 的同步語法，而 `await` 顧名思義就是「等待」，它會確保一個 promise 物件都解決 \( resolve \) 或出錯 \( reject \) 後才會進行下一步，當 async function 的內容全都結束後，會返回一個 promise，這表示後方可以使用`.then`語法來做連接

## 描述

當 async 函式被呼叫時，它會回傳一個 Promise。如果該 async 函式回傳了一個值，Promise 的狀態將為一個帶有該回傳值的 resolved。如果 async 函式拋出例外或某個值，Promise 的狀態將為一個帶有被拋出值的 rejected。

async 函式內部可以使用 await 表達式，它會暫停此 async 函式的執行，並且等待傳遞至表達式的 Promise 的解析，解析完之後會回傳解析值，並繼續此 async 函式的執行。

> async/await 函式的目的在於簡化同步操作 promise 的表現，以及對多個 Promise 物件執行某些操作。就像 Promise 類似於具結構性的回呼函式，同樣地，async/await 好比將 generator 與 promise 組合起來。

## 用法

```javascript
async function a(){
  await b();
  .....       // 等 b() 完成後才會執行
  await c();
  .....       // 等 c() 完成後才會執行
  await new Promise(resolve=>{
    .....
  });
  .....       // 上方的 promise 完成後才會執行
}
a();
a().then(()=>{
  .....       // 等 a() 完成後接著執行
});
```

## 範例

### promise

```javascript
const delay = (s) => {
  return new Promise(resolve => {
    setTimeout(resolve,s); 
  });
};

delay().then(() => {
  console.log(1);     // 顯示 1
  return delay(1000); // 延遲ㄧ秒
}).then(() => {
  console.log(2);     // 顯示 2
  return delay(2000); // 延遲二秒
}).then(() => {
  console.log(3);     // 顯示 3
});
```

### async/await 改寫

```javascript
~async function{           // ~ 開頭表示直接執行這個 function，結尾有 ()
  const delay = (s) => {
    return new Promise(function(resolve){  // 回傳一個 promise
      setTimeout(resolve,s);               // 等待多少秒之後 resolve()
    });
  };

  console.log(1);      // 顯示 1
  await delay(1000);   // 延遲ㄧ秒
  console.log(2);      // 顯示 2
  await delay(2000);   // 延遲二秒
  console.log(3);      // 顯示 3
}();
```

### 搭配promise

```javascript
~async function(){  
  const count = (t,s) => {
      return new Promise(resolve => {
        let a = 0;
        let timer = setInterval(() => {
          console.log(`${t}${a}`);
          a = a + 1;
          if(a>5){
            clearInterval(timer);
            resolve();  // 表示完成
          }
        },s);
      });
    };

  console.log(1); 
  await count('haha', 100);
  console.log(2);
}();
```

輸出:

```text
1
haha0 ~ haha5
2
```

