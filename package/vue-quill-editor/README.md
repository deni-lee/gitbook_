# vue-quill-editor

基於Quill，適用於Vue的富文本編輯器，支持服務端渲染和單頁應用

## 安裝

CDN
```html
<link rel="stylesheet" href="path/to/quill.core.css"/>
<link rel="stylesheet" href="path/to/quill.snow.css"/>
<link rel="stylesheet" href="path/to/quill.bubble.css"/>
<script type="text/javascript" src="path/to/quill.js"></script>
<script type="text/javascript" src="path/to/vue.min.js"></script>
<script type="text/javascript" src="path/to/dist/vue-quill-editor.js"></script>
<script type="text/javascript">
  Vue.use(window.VueQuillEditor)
</script>
```

NPM
```html
npm install vue-quill-editor --save
```

### Nuxt

plugin/vue-quill-editor.js
```js
import Vue from 'vue'
import VueQuillEditor from 'vue-quill-editor'

// require styles
import 'quill/dist/quill.core.css'
import 'quill/dist/quill.snow.css'
import 'quill/dist/quill.bubble.css'

Vue.use(VueQuillEditor, /* { default global options } */)
```
config.js中加入
```js
plugins:[
    { src: '~plugins/vue-quill-editor', ssr: false }
]
```
使用

```js
<template>

  <quill-editor v-model="content">  </quill-editor>

</template>

<script>

  export default {
    data () {
      return {
        content: '',
      }
    },
  }
</script>
```

## 參考文獻
https://github.com/surmon-china/vue-quill-editor vue-quill-editor 官方github

https://quilljs.com/docs/quickstart/ qulli官方

https://gitpress.io/@rainy/vue-quill-editor