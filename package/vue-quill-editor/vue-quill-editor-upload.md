# vue-quill-editor-upload

一個用於在Quill中上傳圖片的插件

🌟插入圖像時上傳圖像，然後將http：// URL替換為base64-URL

🌟預覽正在加載動畫的圖像

🌟上傳圖片時，我們可以繼續編輯內容，包括更改圖片的位置，甚至刪除圖片。

## 安裝

```text
npm install quill-plugin-image-upload --save
```

## 使用

```javascript
import Quill from 'quill';
import 'quill/dist/quill.snow.css';
import imageUpload from 'quill-plugin-image-upload';

// register quill-plugin-image-upload
Quill.register('modules/imageUpload', imageUpload);

new Quill('#editor', {
  theme: 'snow',
  modules: {
    toolbar: [
     'image'
    ],
    imageUpload: {
      upload: file => {
        // return a Promise that resolves in a link to the uploaded image
        return new Promise((resolve, reject) => {
          ajax().then(data => resolve(data.imageUrl));
        });
      }
    },
  },
});
```

## 參考文獻

[https://github.com/dragonwong/quill-plugin-image-upload](https://github.com/dragonwong/quill-plugin-image-upload)

