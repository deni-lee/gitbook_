# vue-fb-customer-chat

Vue.js的Facebook客戶聊天插件

## 安裝
```js
npm install vue-fb-customer-chat // npm 
yarn add vue-fb-customer-chat // yarm
```

## 使用

### vue中使用

```js
import Vue from 'vue'
import VueFbCustomerChat from 'vue-fb-customer-chat'
 
Vue.use(VueFbCustomerChat, {
  page_id: null, //  change 'null' to your Facebook Page ID,
  theme_color: '#333333', // theme color in HEX
  locale: 'en_US', // default 'en_US'
})
```

### nuxt中使用

創建'plugins / vue-fb-customer-chat.js'

```js
import Vue from 'vue'
import VueFbCustomerChat from 'vue-fb-customer-chat'
 
Vue.use(VueFbCustomerChat, {
  page_id: null, //  change 'null' to your Facebook Page ID,
  theme_color: '#333333', // theme color in HEX
  locale: 'en_US', // default 'en_US'
})
```

在nuxt.conf.js文件中為插件部分添加插件

```js
plugins: [
  { src: '~/plugins/vue-fb-customer-chat.js', ssr: false }
],
```

### FB設置、取得ID

![](../../.gitbook/assets/fb1.jpg)

