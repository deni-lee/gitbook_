---
description: 一款開源播放器，並可透過 Plugin 支援RTMP、DASH 與 FLV
---

# vue-plyr

plyr視頻和音頻播放器的Vue組件。

當您想要在Vue應用程序中使用出色的視頻播放器時，這很有用。

它使用sampotts v3 的plyr播放器。

支持的播放器類型：HTML5視頻，HTML5音頻，YouTube（div和漸進增強）和Vimeo（div和漸進增強）。

### plyr的特色是：

* Github 12367 顆星星
* 可透過 Plugin 支援多種格式、協議影片 \( MP4、FLV、HLS、webm、DASH..etc \)
* 可在 HTML5、Flash 間切換
* 支援播放 YouTube 與 Vimeo 影片
* 極為輕量，plyr.min.js 僅有 95.6 KB
* 有 vue-plyr 與 react-plyr 版可使用

## 安裝

```text
yarn add vue-plyr plyr 
npm i vue-plyr plyr
```

## 引入

在plugins文件夾中創建vue-plyr.js

```javascript
import Vue from 'vue'
import VuePlyr from 'vue-plyr/dist/vue-plyr.ssr.js'

// The second argument is optional and sets the default config values for every player.
Vue.use(VuePlyr, {
  plyr: {
    fullscreen: { enabled: false }
  },
  emit: ['ended']
})
```

nuxt.config.js文件應包括以下內容：

```text
export default {
  plugins: [
    '~/plugins/vue-plyr'
  ],
  css: [
    'plyr/dist/plyr.css'
  ]
}
```

## 用法

```markup
<!-- video element -->
<vue-plyr>
  <video poster="poster.png" src="video.mp4">
    <source src="video-720p.mp4" type="video/mp4" size="720">
    <source src="video-1080p.mp4" type="video/mp4" size="1080">
    <track kind="captions" label="English" srclang="en" src="captions-en.vtt" default>
  </video>
</vue-plyr>

<!-- audio element -->
<vue-plyr>
  <audio>
    <source src="audio.mp3" type="audio/mp3"/>
    <source src="audio.ogg" type="audio/ogg"/>
  </audio>
</vue-plyr>

<!-- youtube iframe with progressive enhancement (extra queries after the url to optimize the embed) -->
<vue-plyr>
  <div class="plyr__video-embed">
    <iframe
      src="https://www.youtube.com/embed/bTqVqk7FSmY?iv_load_policy=3&modestbranding=1&playsinline=1&showinfo=0&rel=0&enablejsapi=1"
      allowfullscreen allowtransparency allow="autoplay">
    </iframe>
  </div>
</vue-plyr>

<!-- youtube div element -->
<vue-plyr>
  <div data-plyr-provider="youtube" data-plyr-embed-id="bTqVqk7FSmY"></div>
</vue-plyr>

<!-- vimeo iframe with progressive enhancement (extra queries after the url to optimize the embed) -->
<vue-plyr>
    <div class="plyr__video-embed">
      <iframe
        src="https://player.vimeo.com/video/76979871?loop=false&byline=false&portrait=false&title=false&speed=true&transparent=0&gesture=media"
        allowfullscreen allowtransparency allow="autoplay">
      </iframe>
    </div>
  </vue-plyr>

<!-- vimeo div element -->
<vue-plyr>
  <div data-plyr-provider="vimeo" data-plyr-embed-id="76979871"></div>
</vue-plyr>
```

## 參考文獻

[https://github.com/redxtech/vue-plyr](https://github.com/redxtech/vue-plyr) 官方github

[https://github.com/sampotts/plyr](https://github.com/sampotts/plyr) plyr API

