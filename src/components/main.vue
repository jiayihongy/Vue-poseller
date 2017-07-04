<template>
<div class="main">
  <el-row>
    <el-col :span="7">
      <el-tabs v-model="activeName" @tab-click="handleClick">
        <el-tab-pane label="点餐" name="first">
          <el-table :data="tableData4" border style="width: 100%" max-height="250">
            <el-table-column fixed prop="date" label="日期" width="150">
            </el-table-column>
            <el-table-column prop="name" label="姓名" width="120">
            </el-table-column>
            <el-table-column prop="province" label="省份" width="120">
            </el-table-column>
            <el-table-column prop="city" label="市区" width="120">
            </el-table-column>
            <el-table-column prop="address" label="地址" width="300">
            </el-table-column>
            <el-table-column prop="zip" label="邮编" width="120">
            </el-table-column>
            <el-table-column fixed="right" label="操作" width="120">
              <template scope="scope">
       <el-button
         @click.native.prevent="deleteRow(scope.$index, tableData4)"
         type="text"
         size="small">
         移除
       </el-button>
     </template>
            </el-table-column>
          </el-table>
        </el-tab-pane>
        <el-tab-pane label="挂单" name="second"></el-tab-pane>
        <el-tab-pane label="外卖" name="third"></el-tab-pane>
      </el-tabs>
    </el-col>
    <el-col :span="17">
      <div class="grid-content bg-purple-light">物品栏</div>
    </el-col>
  </el-row>
</div>
</template>

<script>
export default {
  name: 'main',
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.main {}
</style>
