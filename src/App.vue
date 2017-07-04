<template>
<div id="app">
  <!-- 公共左边栏 -->
  <leftnav></leftnav>
  <router-view></router-view>
</div>
</template>

<script>
import leftnav from '@/components/commen/leftnav'
export default {
  name: 'app',
  components: {
    leftnav
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  height: 100%;
}
</style>
