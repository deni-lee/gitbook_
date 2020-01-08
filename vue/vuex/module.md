# Module

## 為什麼需要模塊化
前面我們講到的例子都在一個狀態樹裡進行，當一個項目比較大時，所有的狀態都集中在一起會得到一個比較大的對象，進而顯得臃腫，難以維護。為了解決這個問題，Vuex允許我們將store分割成模組（module），每個module有自己的state，mutation，action，getter，甚至還可以往下嵌套模組

```js
const moduleA = {
  state: { ... },
  mutations: { ... },
  actions: { ... },
  getters: { ... }
}

const moduleB = {
  state: { ... },
  mutations: { ... },
  actions: { ... }
}

const store = new Vuex.Store({
  modules: {
    a: moduleA,
    b: moduleB
  }
})

store.state.a // -> moduleA 的状态
store.state.b // -> moduleB 的状态
```

## 命名空間
上面所有的例子中，模塊內部的action、mutation、getter是註冊在全局命名空間的，如果你在moduleA和moduleB里分別聲明了命名相同的action或者mutation或者getter（叫some），當你使用<code>store. commit('some')</code>，A和B模塊會同時響應。所以，如果你希望你的模塊更加自包含和提高可重用性，你可以添加namespaced: true的方式，使其成為命名空間模塊。當模塊被註冊後，它的所有getter，action，mutation都會自動根據模塊註冊的路徑調用整個命名

