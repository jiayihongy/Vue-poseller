<template>
<div class="main">
  <el-row>
    <el-col :span="7">
      <el-tabs>
        <el-tab-pane label="点餐">
          <el-table :data="tableData" border style="width: 100%">
            <el-table-column prop="goodsName" label="商品"></el-table-column>
            <el-table-column prop="count" label="量" width="50"></el-table-column>
            <el-table-column prop="price" label="金额" width="70"></el-table-column>
            <el-table-column fixed="right" label="操作" width="100">
              <template scope="scope">
                <el-button type="text" size="small">增加</el-button>
                <el-button type="text" size="small">删除</el-button>
              </template>
            </el-table-column>
          </el-table>
          <div class="buttons">
            <el-button type="warning">挂单</el-button>
            <el-button type="danger">删除</el-button>
            <el-button type="success">结账</el-button>
          </div>
        </el-tab-pane>
        <el-tab-pane label="挂单">

        </el-tab-pane>
        <el-tab-pane label="外卖">

        </el-tab-pane>
      </el-tabs>
    </el-col>
    <el-col :span="17">
      <div class="goodslist">
        <div class="title">常点商品</div>
        <ul>
          <li>
            <span>香辣鸡腿堡</span>
            <span>￥15</span>
          </li>
        </ul>
      </div>
    </el-col>
  </el-row>
</div>
</template>

<script>
export default {
  name: 'main',
  data() {
    return {
      tableData: [{
        goodsName: '可口可乐',
        price: 8,
        count: 1
      }, {
        goodsName: '香辣鸡腿堡',
        price: 15,
        count: 1
      }, {
        goodsName: '爱心薯条',
        price: 8,
        count: 1
      }, {
        goodsName: '甜筒',
        price: 8,
        count: 1
      }]
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.main {
    .buttons{
      margin-top: 10px;
    }
    .goodslist{
      .title{
        box-sizing: border-box;
        height: 42px;
        background-color: #F9FAFC;
        text-align: left;
        color:#8492A6;
        line-height: 42px;
        padding-left: 40px;
        border-bottom: 1px solid #D3DCE6;
      }
      ul{
        list-style: none;
        li{
          float: left;
          padding: 10px;
          background-color: #EFF2F7;
          border-radius: 4px;
          span:last-child{
            color:#FF4949;
          }
        }
      }
    }
}
</style>
