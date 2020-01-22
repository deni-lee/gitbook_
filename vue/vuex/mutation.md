# mutation

> 1. 透過commit接收Actions傳遞的資料與行為，並經過計算處理過後改變State。
> 2. 每個Mutation都有一個字串型態的事件類型\(type\)和一個回調函數\(handler\)。
> 3. 回調函數\(handler\)就是我們實際更改狀態的地方，第一個參數即帶入State。
> 4. 注意只有使用commit mutation才能改變在Store中的狀態，這個動作就像是註冊事件一樣，是不可以直接調用mutation handler的。

提交 mutations 是改變 Vuex 中 store 的唯一方式。 mutations 非常類似於組件中的事件（event），每個 mutation 都有一個字串的  事件類型 \(type\) 和一個回調函數 \(handler\)， handler 就是我們實際進行狀態更改的地方，並且他會接受 state 作為第一個參數。

```text
const store = new Vuex.Store({
  state: {
    count: 1
  },
  mutations: {
    increment(state) {
      // 變更狀態
      state.count++;
    }
  }
});
```

不能像調用 state 一樣調用 mutations ，而是要以 store.commit 的方法來做呼叫。 EX:

```javascript
store.commit('increment');
```

## 提交載荷（Payload）

你可以向store.commit傳入額外的參數，即mutation的載荷（payload）：

```javascript
// ...
mutations: {
  increment (state, n) {
    state.count += n
  }
}
store.commit('increment', 10)
```

在大多數情況下，載荷應該是一個對象，這樣可以包含多個字段並且記錄的mutation 會更易讀：

```javascript
// ...
mutations: {
  increment (state, payload) {
    state.count += payload.amount
  }
}
store.commit('increment', {
  amount: 10
})
```

## 在組件中提交 mutations

我們可以在組件中使用 this.$store.commit\('xxx'\) ，提交 mutations 或者使用 mapMutations 輔助函數將組件中的 methods 映射為 store.commit 來調用。

`````js export default { // ... methods: { ...mapMutations([ 'increment', // 將```this.increment\(\)`映射為`this.$store.commit\('increment'\)\`

```text
  // `mapMutations` 也支援 payloads:
  'incrementBy' // 將 `this.incrementBy(amount)` 映射為 `this.$store.commit('incrementBy', amount)`
]),
...mapMutations({
  add: 'increment' // 將 `this.add()` 映射為 `this.$store.commit('increment')`
})
```

} } \`\`

