# vue-carousel

幻燈片組件，用於循環顯示元素（圖像或文本幻燈片），例如輪播。

## 安裝

```text
npm install vue-carousel //npm
yarn add vue-carousel //yarn
```

## 使用

全局 plugin/carousel.js

```javascript
import Vue from 'vue';
import VueCarousel from 'vue-carousel';

Vue.use(VueCarousel);
```

組件中使用

```javascript
<carousel :per-page="1" :navigate-to="someLocalProperty" :mouse-drag="false">
    <slide>
      Slide 1 Content
    </slide>
    <slide>
      Slide 2 Content
    </slide>
</carousel>
```

## 參考文獻

[https://github.com/ssense/vue-carousel\#readme](https://github.com/ssense/vue-carousel#readme) vue-carousel github

[https://getbootstrap.com/docs/4.0/components/carousel/](https://getbootstrap.com/docs/4.0/components/carousel/) boostrap

