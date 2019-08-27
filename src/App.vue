<template>
  <div id="app">
    <keep-alive><router-view/></keep-alive>
    <main-tar-bar/>
  </div>
</template>

<script>
  import MainTarBar from 'components/content/mainTabbar/MainTabBar'
  import NavBar from 'components/common/tabbar/TabBar'
  export default {
    name: 'app',
    components: {
      MainTarBar,
      NavBar
    }
  }
</script>

<style>
  @import "assets/css/base.css";
</style>
