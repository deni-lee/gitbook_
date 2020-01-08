# getter
## 為什麼需要使用 getters ？
在某些時候我們需要 computed store` 中的 state ，例如在 to do list 內取得完成的數量。
```js
computed: {
  doneTodosCount () {
    return this.$store.state.todos.filter(todo => todo.done).length
  }
}
```
但是如果有多個組件要使用相同功能呢？我們要複製上面的程式碼到每個組件內嗎？還是要將他抽取出來成為一個 helper ？其實這兩個做法都不太理想。
## getters 使用方式
還好， Vuex 允許我們在 store 中定義 getters ，getters 就類似組件中的 computed ， getters 的返回值會根據他依賴的關係被緩存起來，只有當他依賴的值發生改變才會重新被計算。

## magGetters 輔助函數
mapGetters 輔助函數與前面提到的 mapState 用法相近，可以簡化程式碼。
```js
<template>
  <div>
    <div>{{doneTodos}}</div>
    <div>{{doneTodosCount}}</div>
  </div>
</template>

<script>
import { mapGetters } from 'vuex';

export default {
  computed: {
    mapGetters([
      'doneTodos',
      'doneTodosCount',
    ]),
  },
};
</script>
//Output: [ { “id”: 1, “text”: “…”, “done”: true } ], 1
```

如果我們要將 getters 屬性取另外一個名稱，可以用物件的方式：

新名稱: ‘getters 屬性名稱’
```js
computed: mapGetters({
  // 映射 `this.doneCount` 為 `store.getters.doneTodosCount`
  doneCount: 'doneTodosCount'
}),
```