<template>
  <div id="app">
    <img src="./assets/logo.png">
    <ul>
      <!-- 使用 router-link 组件来导航. -->
      <!-- 通过传入 `to` 属性指定链接. -->
      <!-- <router-link> 默认会被渲染成一个 `<a>` 标签 -->
      <li><router-link to="/first">点我跳转第一个页面（静态模板）</router-link></li>
      <li><router-link to="/hello">点我跳转第二个页面（import 模板todoList）</router-link></li>
      <li><router-link to="/ajax">点我跳转第三个页面（ajax外部数据渲染模板）</router-link></li>
    </ul>
    <!-- 路由出口 -->
    <!-- 路由匹配到的组件将渲染在这里 -->
    <router-view></router-view>
    <!-- <hello msgfromfather = "I am your father components"></hello> -->
  </div>
</template>

<!-- <script>
//不用vue-router路由时  如果需要在此处显示其他模板中的内容，需要将这个文件import进来
/*import Hello from './components/Hello'

export default {
  name: 'app',
  components: {
    Hello
  }
}*/
</script> -->

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
