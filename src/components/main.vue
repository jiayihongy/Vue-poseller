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
                <el-button type="text" size="small" @click="addToList(scope.row)">增加</el-button>
                <el-button type="text" size="small" @click="removeList(scope.row)">删除</el-button>
              </template>
            </el-table-column>
          </el-table>
          <div class="zongshu">
            <small>总计：</small><span>{{allCount}}</span>
            <small>总价：</small><span>{{allPrice}}</span>
          </div>
          <div class="buttons">
            <el-button type="warning">挂单</el-button>
            <el-button type="danger" @click="removeAllList">重选</el-button>
            <el-button type="success" @click="checkOut">结账</el-button>
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
          <li v-for="good in goods" @click="addToList(good)">
            <span>{{good.goodsName}}</span>
            <span>￥{{good.price}}</span>
          </li>
        </ul>
      </div>
      <div class="goodsdetail">
        <el-tabs>
          <el-tab-pane label="汉堡">
            <ul>
              <li v-for="hanbao in goodstyle1" @click="addToList(hanbao)">
                <div class="left-img">
                  <img :src="hanbao.goodsImg" alt="">
                </div>
                <div class="right-price">
                  <p>{{hanbao.goodsName}}</p>
                  <p>￥{{hanbao.price}}</p>
                </div>
              </li>
            </ul>
          </el-tab-pane>
          <el-tab-pane label="小食">
            <ul>
              <li v-for="hanbao in goodstyle2" @click="addToList(hanbao)">
                <div class="left-img">
                  <img :src="hanbao.goodsImg" alt="">
                </div>
                <div class="right-price">
                  <p>{{hanbao.goodsName}}</p>
                  <p>￥{{hanbao.price}}</p>
                </div>
              </li>
            </ul>
          </el-tab-pane>
          <el-tab-pane label="饮料">
            <ul>
              <li v-for="hanbao in goodstyle3" @click="addToList(hanbao)">
                <div class="left-img">
                  <img :src="hanbao.goodsImg" alt="">
                </div>
                <div class="right-price">
                  <p>{{hanbao.goodsName}}</p>
                  <p>￥{{hanbao.price}}</p>
                </div>
              </li>
            </ul>
          </el-tab-pane>
          <el-tab-pane label="套餐">
            <ul>
              <li v-for="hanbao in goodstyle4" @click="addToList(hanbao)">
                <div class="left-img">
                  <img :src="hanbao.goodsImg" alt="">
                </div>
                <div class="right-price">
                  <p>{{hanbao.goodsName}}</p>
                  <p>￥{{hanbao.price}}</p>
                </div>
              </li>
            </ul>
          </el-tab-pane>
        </el-tabs>
      </div>
    </el-col>
  </el-row>
</div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'main',
  data() {
    return {
      tableData: [],
      goods:[],
      goodstyle1:[],
      goodstyle2:[],
      goodstyle3:[],
      goodstyle4:[],
      allPrice:0,
      allCount:0
    }
  },
  methods:{
    addToList(data){
      var ishave = false;
      //判断库里有没有这个商品
      for(let i = 0;i<this.tableData.length;i++){
        if(this.tableData[i].goodsName == data.goodsName){
          ishave = true;
        }
      }
      //如果有，则数量加加，如果没有，这新增一个
      if(ishave){
        let arr = this.tableData.filter(o => o.goodsName == data.goodsName);
        arr[0].count++;
      }else{
        let newGood = {goodsName:data.goodsName,count:1,price:data.price};
        this.tableData.push(newGood);
      }
      this.countList();


    },
    removeList(data){
      this.tableData = this.tableData.filter(o => o.goodsName !== data.goodsName);
      this.countList();
    },
    countList(){
      this.allPrice = 0;
      this.allCount = 0;
      this.tableData.forEach(o => {
        this.allCount += o.count ;
        this.allPrice = this.allPrice + (o.count*o.price);
      })
    },
    removeAllList(){
      this.tableData.length = 0;
      this.allPrice = 0;
      this.allCount = 0;
    },
    checkOut(){
      this.$message({
          message: '点餐成功，请耐心等待哟~',
          type: 'success'
        });
    }
  },
  created(){
    axios.get('http://jspang.com/DemoApi/oftenGoods.php')
    .then(res=>{
      this.goods = res.data;
    })
    .catch(err=>{
      alert('狗屁不通!')
    });
    axios.get('http://jspang.com/DemoApi/typeGoods.php')
    .then(res=>{
      this.goodstyle1 = res.data[0];
      this.goodstyle2 = res.data[1];
      this.goodstyle3 = res.data[2];
      this.goodstyle4 = res.data[3];
    })
    .catch(err=>{
      alert('狗屁不通!')
    });
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.main {
    .buttons{
      margin-top: 10px;
    }
    .zongshu{
      background-color: rgb(133, 133, 133);
      color:#fff;
      padding:4px;
      span:nth-of-type(1){
        margin-right: 50px;
      }
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
          border: 1px solid rgb(176, 176, 176);
          border-radius: 4px;
          margin-left: 10px;
          margin-top: 10px;
          color:rgb(68, 68, 68);
          cursor: pointer;
          span:last-child{
            color:#FF4949;
          }
        }
      }
    }
    .goodsdetail{
      clear: both;
      ul{
        list-style: none;
        li{
          float: left;
          background: linear-gradient(to top, rgb(249, 255, 133) , rgb(246, 252, 216));
          margin: 10px;
          padding: 4px;
          border-radius: 4px;
          width: 23%;
          cursor:pointer;
          .left-img{
            float: left;
            border-radius: 10px;
            width: 40%;
            font-size: 0;
            img{
              border-radius: 4px;
              width: 100%;
              height: 100%;
            }
          }
          .right-price{
            float: left;
            width: 60%;
          }
        }
      }
    }

}
</style>
