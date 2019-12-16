---
description: Vue I18n 是 Vue.js 的國際化插件。它可以輕鬆地將一些本地化功能集成到你的 Vue.js 應用程序中。
---

# vue-i18n

要讓網站也可以提供給外籍人士使用，不可免俗的需要多國語系的支援，因此本文透過 vue-i18n 來打造一個多國語系網站，並介紹基本的使用情境及用法。

## 安裝

```text
npm install vue-i18n --save
```

## 使用範例

### HTML

```markup
<script src="https://unpkg.com/vue/dist/vue.js"></script>
<script src="https://unpkg.com/vue-i18n/dist/vue-i18n.js"></script>

<div id="app">
  <p>{{ $t("message.hello") }}</p>
</div>
```

### JavaScript

```javascript
// 如果使用模块系统 (例如通过 vue-cli)，则需要导入 Vue 和 VueI18n ，然后调用 Vue.use(VueI18n)。
// import Vue from 'vue'
// import VueI18n from 'vue-i18n'
//
// Vue.use(VueI18n)

// 准备翻译的语言环境信息
const messages = {
  en: {
    message: {
      hello: 'hello world'
    }
  },
  ja: {
    message: {
      hello: 'こんにちは、世界'
    }
  }
}

// 通过选项创建 VueI18n 实例
const i18n = new VueI18n({
  locale: 'ja', // 设置地区
  messages, // 设置地区信息
})


// 通过 `i18n` 选项创建 Vue 实例
new Vue({ i18n }).$mount('#app')

// 现在应用程序已经准备好了！
```

### 輸出結果

```javascript
<div id="#app">
  <p>こんにちは、世界</p>
</div>
```

## 參考文獻

[https://kazupon.github.io/vue-i18n/zh/introduction.html\#%E8%B5%9E%E5%8A%A9%E5%95%86](https://kazupon.github.io/vue-i18n/zh/introduction.html#%E8%B5%9E%E5%8A%A9%E5%95%86) 官方文檔

[https://ithelp.ithome.com.tw/articles/10194177](https://ithelp.ithome.com.tw/articles/10194177)

[https://dotblogs.com.tw/wasichris/2018/05/12/012517](https://dotblogs.com.tw/wasichris/2018/05/12/012517)

