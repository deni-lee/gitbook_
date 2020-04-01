# modal

模態框（Modal）是覆蓋在父窗體上的子窗體。通常，目的是顯示來自一個單獨的源的內容，可以在不離開父窗體的情況下有一些互動。子窗體可提供信息、交互等

模態得到了簡化，但是由JavaScript和CSS驅動的靈活對話框提示。它們支持從用戶通知到完全自定義內容的許多用例，並具有少量有用的子組件，大小，變體，可訪問性等。

範例：

```js
<div>
  <b-button v-b-modal.modal-1>Launch demo modal</b-button>

  <b-modal id="modal-1" title="BootstrapVue">
    <p class="my-4">Hello from modal!</p>
  </b-modal>
</div>
```

## 彈窗版面

- <code>&lt;b-modal&gt;</code>默認情況下，頁腳中有<mark>確定</mark>和<mark>取消</mark> 按鈕。
可以自定義按鈕的大小，禁用按鈕，隱藏“ 取消”按鈕
- <code>&lt;b-modal&gt;</code>支持在ESC上關閉，在背景幕點擊時關閉以及X標題中的關閉按鈕。這些特徵可以通過設置道具被禁用
- 可以通過命名的插槽覆蓋模式標題，通過插槽<code>modal-title</code>完全覆蓋標題<code>modal-header</code>，並通過<code>modal-footer</code>插槽完全覆蓋頁腳。
**注意**：使用<code>modal-footer</code>插槽時，將不顯示默認的“ 確定”和“ 取消”按鈕。另外，如果使用<code>modal-header</code>插槽，X則不會顯示默認的頁眉關閉按鈕，也無法使用<code>modal-title</code>插槽。


##切換模式可見性
您可以採用多種方法來切換的可見性<code>&lt;b-modal&gt;</code>

### 使用v-b-modal指令

**範例：** 
```js
<div>
  <!-- Using modifiers -->
  <b-button v-b-modal.my-modal>Show Modal</b-button>

  <!-- Using value -->
  <b-button v-b-modal="'my-modal'">Show Modal</b-button>

  <!-- The modal -->
  <b-modal id="my-modal">Hello From My Modal!</b-modal>
</div>
```

一旦模式關閉，此方法將自動將焦點返回到觸發元素（類似於默認的Bootstrap功能）。切換模式可見性的其他方法可能需要其他代碼才能實現此可訪問性功能。

[**常用指令**](https://bootstrap-vue.js.org/docs/components/modal/#accessibility)

@ok ：點擊確定觸發的事件

@hidden：關閉model 觸發的事件　

ok-title="保存"：確定按鈕的text

cancel-titile="關閉"：關閉按鈕的text

:no-close-on-backdrop="布爾值"：點擊背景是否關閉model

hide-footer：隱藏底部“確定、關閉”按鈕
hide-header: 隱藏頭部

hide-header-close：隱藏右上方"x"

### 使用<code>this.\$bvModal.show()</code>和<code>this.\$bvModal.hide()</code>實例方法

當BootstrapVue作為插件安裝或使用ModalPlugin插件時，BootstrapVue將向<code>\$bvModal</code>每個Vue實例（組件，應用程序）注入一個對象。<code>this.\$bvModal</code>公開了幾種方法，其中兩種用於顯示和隱藏模式：

| 方法                 | 描述           |
|----------------------|----------------|
|this.$bvModal.show(id)|顯示指定的模態 id|
|this.$bvModal.hide(id)|隱藏指定的模態 id|

這兩種方法在被調用後都會立即返回。

```js
<div>
  <b-button id="show-btn" @click="$bvModal.show('bv-modal-example')">Open Modal</b-button>

  <b-modal id="bv-modal-example" hide-footer>
    <template v-slot:modal-title>
      Using <code>$bvModal</code> Methods
    </template>
    <div class="d-block text-center">
      <h3>Hello From This Modal!</h3>
    </div>
    <b-button class="mt-3" block @click="$bvModal.hide('bv-modal-example')">Close Me</b-button>
  </b-modal>
</div>
```

### 使用<code>show()</code>，<code>hide()</code>以及<code>toggle()</code>組件的方法

您可以訪問模式使用ref屬性，然後調用show()，hide()或toggle()方法。

```js
<template>
  <div>
    <b-button id="show-btn" @click="showModal">Open Modal</b-button>
    <b-button id="toggle-btn" @click="toggleModal">Toggle Modal</b-button>

    <b-modal ref="my-modal" hide-footer title="Using Component Methods">
      <div class="d-block text-center">
        <h3>Hello From My Modal!</h3>
      </div>
      <b-button class="mt-3" variant="outline-danger" block @click="hideModal">Close Me</b-button>
      <b-button class="mt-2" variant="outline-warning" block @click="toggleModal">Toggle Me</b-button>
    </b-modal>
  </div>
</template>

<script>
  export default {
    methods: {
      showModal() {
        this.$refs['my-modal'].show()
      },
      hideModal() {
        this.$refs['my-modal'].hide()
      },
      toggleModal() {
        // We pass the ID of the button that we want to return focus to
        // when the modal has hidden
        this.$refs['my-modal'].toggle('#toggle-btn')
      }
    }
  }
</script>
```

### 使用<code>v-model</code>屬性

v-model屬性始終會自動與<b-modal>可見狀態同步，您可以使用來顯示/隱藏v-model。

```js
<template>
  <div>
    <b-button @click="modalShow = !modalShow">Open Modal</b-button>

    <b-modal v-model="modalShow">Hello From Modal!</b-modal>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        modalShow: false
      }
    }
  }
</script>
```

