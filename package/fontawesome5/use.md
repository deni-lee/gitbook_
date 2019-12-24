# 使用

## Nuxt.js

### 配置

plugin 下新增 fontawesome.js

```javascript
import Vue from 'vue'
// the component
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'
// icon 要使用的標籤名稱 <font-awesome-icon>
Vue.component('font-awesome-icon', FontAwesomeIcon)
Vue.config.productionTip = false
```

nuxt.config.js

```javascript
    modules: [
        'nuxt-fontawesome',
    ],
    fontawesome: {
        // icon 的標籤使用 <fa>，這邊不設定就會依照 plugin 裡的設定<font-awesome-icon>
        component: 'fa',
        imports: [
            // 引入 fas 所有的icon
            {
                set: '@fortawesome/free-solid-svg-icons',
                icons: ['fas']
            },
            {
                set: '@fortawesome/free-brands-svg-icons',
                icons: ['fab']
            },
        ]
    },
    plugins: [
        '@/plugins/fontawesome.js'
    ],
```

### 使用圖示

```javascript
<fa :icon="['類別', 'icon名稱']" />  <br>
```

```javascript
<template>
<div>
  <fa :icon="['fas', 'calculator']" />  <br>
</div>
</template>
```

## js

### 載入

把 svg-with-js 的資料夾複製一份到你的專案資料夾中（或者也可以直接使用 FontAwesome CDN），接著載入 JS 的方式非常簡單，就和過去載入 CSS 一樣，官方建議放在 內：

```javascript
<!-- 一次載入所有的圖示 -->
<script defer src="https://use.fontawesome.com/releases/v5.0.0/js/all.js"></script>
```

```javascript
<!-- 選擇所需圖示類型的載入 -->
<!-- 這裡會載入 solid 和 regular 這兩類的圖示，最後要記得載入 fontawesome.js -->
<script src="https://use.fontawesome.com/releases/v5.0.0/js/solid.js"></script>
<script src="https://use.fontawesome.com/releases/v5.0.0/js/regular.js"></script>
<script src="https://use.fontawesome.com/releases/v5.0.0/js/fontawesome.js"></script>
```

### 使用圖示

圖示的使用幾乎和過去一樣，在 HTML 中透過 `<i>` 標籤同時給予不同的 class 就會產生不同的圖示

```javascript
<i class="fas fa-camera-retro"></i>
```

