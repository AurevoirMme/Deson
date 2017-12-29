<template>
<div id="app">
  <img src="./assets/logo.png">
  <h1>{{ msg }}</h1>
  <div v-html="message"></div>
  <hellocomponent></hellocomponent>

  <label for="r1">修改颜色</label><input type="chexbox" v-model="class1" id="r1">
  <br><br>
  <div v-bind:class="{'class1':class1}">
    directiva v-bind:class
  </div>

  {{5+5}}<br> {{ ok ? 'YES' : 'NO' }}<br> {{ message.split('').reverse().join('') }}
  <div v-bind:id="'list-' + id">菜鸟教程</div>

  <p v-if="seen">现在你看到我了</p>

  <pre><a v-bind:href="url">菜鸟教程</a></pre>

  <p>{{ message }}</p>
  <input v-model="message">

   <!-- 完整语法 -->
   <button v-on:click="reverseMessage">反转字符串</button>
   <!-- 缩写 -->
   <button @click="reverseMessage">反转字符串</button>


   <!-- 在两个大括号中 -->
{{ message | capitalize }}

<!-- 在 v-bind 指令中 -->
<div v-bind:id="rawId | formatId"></div>

<!-- 完整语法 -->
<a v-bind:href="url">菜鸟教程</a>
<!-- 缩写 -->
<a :href="url">菜鸟教程</a>

</div>
</template>

<script>
import hellocomponent from './components/hello.vue'
export default {
  name: 'app',
  data() {
    return {
      msg: 'Welcome to Your Vue.js App',
      message: '<h1>Vue.js学习</h1>',
      class1: false,
      ok: true,
      message: 'runoob!',
      id: 1,
      seen: false,
      url: 'http://www.runoob.com'
    }
  },
  components: {
    hellocomponent
  },
  methods: {
    reverseMessage: function () {
      this.message = this.message.split('').reverse().join('')
    }
  },
  filters: {
    capitalize: function (value) {
      if (!value) return ''
      value = value.toString()
      return value.charAt(0).toUpperCase() + value.slice(1)
    }

  }
}
</script>

<style lang="scss">
#app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}

h1,
h2 {
    font-weight: normal;
}

ul {
    list-style-type: none;
    padding: 0;
}

li {
    display: inline-block;
    margin: 0 10px;
}

a {
    color: #42b983;
}
</style>
