# vform

在Vue中處理Laravel後端驗證的一種簡單方法。受Laravel Spark啟發。

## 安裝
```
npm i axios vform
```

## 用法
### Components for Bootstrap 3 and 4.

**!!!NUXT!!! ->plugins/vform.js**

```js
import { 
  HasError,
  AlertError,
  AlertErrors, 
  AlertSuccess
} from 'vform'

Vue.component(HasError.name, HasError)
Vue.component(AlertError.name, AlertError)
Vue.component(AlertErrors.name, AlertErrors)
Vue.component(AlertSuccess.name, AlertSuccess)
```

### has-error
Display the validation error for a field.
```js
<!-- Bootstrap 4 -->
<div class="form-group">
  <label>Username</label>
  <input v-model="form.username" type="text" name="username"
    class="form-control" :class="{ 'is-invalid': form.errors.has('username') }">
  <has-error :form="form" field="username"></has-error>
</div>

<!-- Bootstrap 3 -->
<div class="form-group" :class="{ 'has-error': form.errors.has('username') }">
  <label>Username</label>
  <input v-model="form.username" type="text" name="username" class="form-control">
  <has-error :form="form" field="username"></has-error>
</div>
```
### alert-error
Show a danger alert if there are any errors.
```js
<alert-error :form="form" message="There were some problems with your input."></alert-error>
```

### usage
```js
<template>
<div id="app">
  <form @submit.prevent="login" @keydown="form.onKeydown($event)">
    <div class="form-group">
      <label>Username</label>
      <input v-model="form.username" type="text" name="username"
        class="form-control" :class="{ 'is-invalid': form.errors.has('username') }">
      <has-error :form="form" field="username"></has-error>
    </div>
 
    <div class="form-group">
      <label>Password</label>
      <input v-model="form.password" type="password" name="password"
        class="form-control" :class="{ 'is-invalid': form.errors.has('password') }">
      <has-error :form="form" field="password"></has-error>
    </div>
 
    <button :disabled="form.busy" type="submit" class="btn btn-primary">Log In</button>
  </form>
</div>  
</template>
 
<script>
import Vue from 'vue'
import { Form, HasError, AlertError } from 'vform'
 
Vue.component(HasError.name, HasError)
Vue.component(AlertError.name, AlertError)
 
new Vue({
  el: '#app',
  
  data () {
    return {
      // Create a new form instance
      form: new Form({
        username: '',
        password: '',
        remember: false
      })
    }
  },
 
  methods: {
    login () {
      // Submit the form via a POST request
      this.form.post('/login')
        .then(({ data }) => { console.log(data) })
    }
  }
})
</script>
```