<template>
<div id="app">
  <!-- 公共左边栏 -->
  <leftnav></leftnav>
  <!-- 右侧主界面 -->
  <div class="main">
    <router-view></router-view>
  </div>
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

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  height: 100%;
  min-width: 900px;
  .main{
    width: 95%;
    height: inherit;
    float: left;
  }
}
</style>
