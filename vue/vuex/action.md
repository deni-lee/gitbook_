# action
> 1. 定義整個App的所有行為，使用者在前端元件觸發的事件會dispatch給Actions，接著Actions會去commit mutation，進而讓相對應的mutation handler去做更改狀態的動作。
>2. 在這個階段因為常要從後端讀取資料，所以也可以進行非同步地跟Backend API溝通。
## 使用action
Action 類似於mutation，不同在於：

- Action 提交的是mutation，而不是直接變更狀態。
- Action 可以包含任意異步操作。

EX:
```js
const store = new Vuex.Store({
  state: {
    count: 0
  },
  mutations: {
    increment (state) {
      state.count++
    }
  },
  actions: {
    increment (context) {
      context.commit('increment')
    }
  }
})
```
## 簡化程式碼
在實際情況中，我們常會使用 ES2015 中的 參數解構 來簡化程式碼：
```js
actions: {
  increment ({ commit }) {
    commit('increment')
  }
}
```
## 調用 Actions
Action 透過 store.dispatch 方法觸發：
```js
store.dispatch("increment");
```
這樣看起來跟 mutations 的用法差不多，但是我們要記得 mutations 必須是同步執行，而 actions 則可以異步執行。
```js
actions: {
  incrementAsync ({ commit }) {
    setTimeout(() => {
      commit('increment')
    }, 1000)
  }
}
```
## Payload
actions 同樣可以使用 payload 或物件的形式：
```js
// 以 payload 形式分發
store.dispatch("incrementAsync", {
  amount: 10
});

// 以物件形式分發
store.dispatch({
  type: "incrementAsync",
  amount: 10
});
```
## mapActions
我們可以在組件中使用 this.$store.dispatch('xxx') 分發 action，或者 使用 mapActions 輔助函數將組件的 methods 映射為 store.dispatch 調用。
```js
import { mapActions } from "vuex";

export default {
  // ...
  methods: {
    ...mapActions([
      "increment", // 將 `this.increment()` 映射為 `this.$store.dispatch('increment')`

      // `mapActions` 也支持载荷：
      "incrementBy" // 將 `this.incrementBy(amount)` 映射為 `this.$store.dispatch('incrementBy', amount)`
    ]),
    ...mapActions({
      add: "increment" // 將 `this.add()` 映射為 `this.$store.dispatch('increment')`
    })
  }
};
```
## mutation & action 比較

Actions跟Mutations有點相似，跟事件處理都相關，但是它們兩者還是有不一樣的地方：

比較	     | Actions	   | Mutations
------------|:----------:|:------------:
更改狀態	| Actions只能透過commit mutation去提交事件，不能直接更改狀態。|	Mutations透過mutation handler直接實際更改狀態。
處理的事件種類 |	可同時處理非同步事件(call API)，這樣就可以在此階段等待API回應的時間，接收到的資料再commit給Mutations，Mutations收到的資料就會是即時的。|	只能處理同步事件。