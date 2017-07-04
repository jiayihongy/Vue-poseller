<template>
<div class="leftnav">
  <el-row>
    <el-col>
      <el-menu default-active="2">
        <el-menu-item index="1"><i class="icon iconfont icon-hanbao"></i><p>主食</p></el-menu-item>
        <el-menu-item index="2"><i class="icon iconfont icon-shipinyinliao"></i><p>饮料</p></el-menu-item>
        <el-menu-item index="3"><i class="icon iconfont icon-xiai"></i><p>喜欢</p></el-menu-item>
        <el-menu-item index="4"><i class="icon iconfont icon-gouwucheman"></i><p>购物车</p></el-menu-item>
        <el-menu-item index="5"><i class="icon iconfont icon-shengriliwu"></i><p>积分</p></el-menu-item>

      </el-menu>
    </el-col>
  </el-row>
</div>
</template>

<script>
export default {
  name: 'leftnav',
  data() {
    return {

    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.leftnav {
    height: 100%;
    width: 5%;
    .el-row{
      height: inherit;
      .el-col{
        height: inherit;
        .el-menu{
          height: inherit;
          background-color: #ff4949;
          .el-menu-item{
            height: auto;
            line-height: normal;
            padding: 15px 0 !important;
            color:#fff;
            &.is-active{
              color:yellow;
            }
            &:hover{
              background-color: #f7ba2a;
            }
            p{
              margin:0;
              line-height: 150%;
            }
            i{
              font-size: 30px;
            }
          }
        }
      }
    }

}
</style>
