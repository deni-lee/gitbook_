# state

> 1. 用一個物件型態記錄整個App的所有狀態。
> 2. 讓Mutation去更改狀態。
> 3. 雖然建議是將App的所有狀態全部放入Store，但是Vuex還是保有彈性，可以讓元件保有自己的局部狀態。

## 單一狀態樹 \(Single State Tree\)

Vuex 使用單一狀態樹，這是一個物件包含了全部應用層的狀態與供應單一數據來源 \(Single source of truth\)，這代表通常你每個應用只會有一個 store 。單一狀態樹讓我們可以直接指定 state 其中的一項並讓我們能夠輕鬆的得到目前應用程式的狀態與快照 \(snapshots\)。

## 在組件中取得 Vuex 的 state

### 1.  store.state.count

任何的子組件就可以用下面的方式來取得 store 內的 state :

```javascript
export default {
  created() {
    console.log(this.$store.state.count);
  }
};
```

如果我們要如何更好的顯示狀態， 用 computed 來將 state 的狀態存起來會是一個很棒的方式。

```javascript
<template>
  <div>{{count}}</div>
</template>

<script>
export default {
  computed: {
    count() {
      return this.$store.state.count;
    },
  },
};
</script>
```

### 2. mapState 輔助函數

當一個組件需要獲取多個 state 的時候，如果每次都要宣告為 computed 會很麻煩，為了解決這個問題 Vuex 讓我們可以使用 mapState 輔助函數來幫助我們，將繁瑣的流程簡化。

#### 使用方式

```javascript
<template>
  <div>
    <div>{{count}}</div>
    <div>{{countAlias}}</div>
    <div>{{countPlusLocalState}}</div>
  </div>
</template>

<script>
import { mapState } from 'vuex';

export default {
  data() {
    return {
      localCount: 2,
    };
  },
  computed: mapState({

    // 箭頭函數可以使程式碼更簡潔
    count: state => state.count,

    // 直接傳送字串'count'，等同於 `state => state.count`
    countAlias: 'count',

    // 為了使用 `this` 來取得組件內的狀態，必須要使用下列特殊的格式
    countPlusLocalState(state) {
      return state.count + this.localCount;
    },
  }),
};
</script>
```

### 更簡單的使用方式：

```javascript
computed: mapState([
  // 將 this.count 映射為 store.state.count
  'count'
])
```

