# 實作

## 1、安裝

```text
# npm 
npm install dotenv

# Yarn 
yarn add dotenv
```

## 2、在nuxt.config.js中，要求並配置dotenv。

```javascript
require('dotenv').config()
```

## 3、在根目錄下建立 .env 檔案

```text
// 設定key和value
test_1= test
HOST=5555
```

## 4、store下宣告state變數

```javascript
import Vue from 'vue'

export const state = () => ({
    TEST: process.env.test_1
    host: process.env.HOST
})
```

## 5、頁面上使用

```javascript
<div>
  <p> {{ $store.state.host }} </p>
</div>
</template>

<script>
</script>
```

