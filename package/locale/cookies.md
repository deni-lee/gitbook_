# cookies

可設定失效時間。 預設是關閉瀏覽器後失效

* cookie大小限制在4K左右，不適應存業務數據。
* cookie每次隨HTTP事務有一起發送，浪費寬頻。

## ➤ js-cookies

js-cookie外掛是一個JS操作cookie的外掛，原始檔只有3.34 KB，非常輕量級，寫法簡化，使用起來更快速方便

### 1、引入js-cookie.js

* cdn

  ```text
  <script src = ”https://cdn.jsdelivr.net/npm/js-cookie@2/src/js.cookie.min.js”></script>
  ```

* 本地下載下來後：

  ```text
  <script src=”/path/to/js.cookie.js”></script>
  ```

* 模組化開發時:

```javascript
import Cookies from ‘js-cookie’
```

### 2、js-cookie.js常用的API和方法

* 設定cookie

  ```javascript
  Cookies.set('name', 'value', { expires: 7, path: '' });//7天過期
  ```

* 讀取cookie

  ```javascript
  Cookies.get('name');//獲取cookie
  Cookies.get(); #讀取所有的cookie
  ```

* 刪除cookie

  ```javascript
  Cookies.remove('name');
  ```

### 3、實作

[https://github.com/deni-lee/practice/tree/master/cookies](https://github.com/deni-lee/practice/tree/master/cookies)

