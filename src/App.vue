<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">首页</router-link> |
      <router-link to="/github">Github</router-link>
    </div>
    <router-view/>
    <el-footer style="bottom: 0">
      <i style="color: #0d0d0d">Copyright @2020
        <i class="hidden-sm-and-down">All rights reserved made by </i>
        <i style="color: dodgerblue">Xinyuan Huang</i>
      </i>
    </el-footer>
  </div>
</template>

import 'element-ui/lib/theme-chalk/display.css';

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}

.el-footer {
  text-align: center;
  line-height: 60px;
  position: absolute;
  left: 0;
  right: 0;
  bottom: 0;
}
</style>
