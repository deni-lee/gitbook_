# 配置

## transformRequest / transformResponse

**transformRequest**
>只能用在 'PUT', 'POST' 和 'PATCH' 这幾個請求方法，用來在發出 request 前先對要傳的 data 做處理。要注意的是值必須是 array，裡面放 function。

什麼時候會用到？EX用來驗證的 token 不放在 header 裡，而是跟資料塞一起丟給 server，就要像這樣處理：
```js
transformRequest: [].concat(data => {
  const token = Cookies.get('token');
  const mergedData = $.extend(true, data, { token });
  return mergedData;
}),
```
**transformResponse**
>在進入 then / catch 前可作資料處理

## Interceptors
與transformRequest稍微不同，interceptors 可攔截 request 或 response，在<code>then()</code>或<code>catch()</code>之前做些判斷。

例如 API 總是檢查登入狀態，會在錯誤時回傳的 JSON 包個 error: 'login failed'。我們只需檢查這個 key， 直接讓它 throw error 到 catch() 裡面進行後續處理。
## headers
>是即將被發送的自定義標頭
```js
headers: {'X-Requested-With': 'XMLHttpRequest'},
```
## params
>此為 URL 上要代的參數  ~url?ID=123
```js
params: {
    ID: 12345
  },
```
## paramsSerializer
>序列化參數 ???
```js
paramsSerializer: function(params) {
      return Qs.stringify(params, {arrayFormat: 'brackets'})
    },
```
## timeout
>請求時間超過 'timeout'時間，請求會被中止
```js
timeout: 1000,
```
## withCredentials
>用來判斷是否為 跨域存取 (cross-site Access-Control requests)<br>
>等同 Access-Control-Allow-Credentials 表頭<br>
>用來解決 CORS
```js
withCredentials: false, // 默認
```
## <mark>adapter </mark>
>允許自定義處理請求，可讓測試更容易<br> 
>return promise 並提供有效的回應 (valid response)
```js
adapter: function (config) {
    /* ... */
  },
```
## auth
>等同 Authorization 表頭<br>
>如果使用 token 應去 header 設置 Authorization 而非使用此
```js
auth: {
    username: 'janedoe',
    password: 's00pers3cret'
  },
```
## responseType
>伺服器回應的數據類型
```js
伺服器回應的數據類型
```
## <mark>xsrfCookieName/xsrfHeaderName</mark>
>xsrf token 的 Cookie名 / Header名
```js
xsrfCookieName: 'XSRF-TOKEN', 
xsrfHeaderName: 'X-XSRF-TOKEN',
```
## onUploadProgress/onDownloadProgress
>在上傳、下載途中可執行的事情 (progressBar、Loading)
```js
onUploadProgress(progressEvt) { /* 原生 ProgressEvent */  },
    onDownloadProgress(progressEvt) { /* 原生 ProgressEvent */ },
```
## maxContentLength
>限制傳送大小
```js
maxContentLength: 2000, 
```
## validateStatus#
>用來判斷是否解析 Promise 的 狀態碼範圍
```js
validateStatus: function (status) {
      return status >= 200 && status < 300; // default
    },
```
## maxRedirects
>定義 node.js 中要遵循的重定項最大數量
```js
maxRedirects: 5,
```
## httpAgent/httpsAgent
>用於 node.js中執行 http/https的自定義代理<br>   /
>默認不啟用，可配置成 keepAlive
```js
httpAgent: new http.Agent({ keepAlive: true }),
httpsAgent: new https.Agent({ keepAlive: true }),
```
## proxy
>定義 代理伺服器的 Host、Port號<br>
>auth 代表 HTTP Basic auth 應用於連接代理，並提供 credentials<br>
>會設置 Proxy-Authorization 表頭
```js
proxy: {
      host: '127.0.0.1',
      port: 9000,
      auth: {
        username: 'mikeymike',
        password: 'rapunz3l'
      }
    },
```
## cancelToken
>用來取消請求的 token
```js
cancelToken: new CancelToken(function (cancel) {
    })
```