<template>
  <div class="wrap">
    <div class="sum" v-for="(item,index) in commends" :key="index">
      <img :src="item.picUrl" alt="" class="imgbox" />  
      <span></span>
      <a class="tit" href="#">{{item.name}}</a>
      <button class="play"><span class="ear"></span>{{item.playCount}}万 <a href="#" ></a></button>
    </div>
  </div>
</template>
<script>
import axios from "../plugins/axios.js"; /*引入封装的axios*/
export default {
    data() {
    return {
      commends: "",
    };
  },
  created(){
     this.getWangyi()
  },
  methods:{
      getWangyi() {
      axios({
        url: "/personalized?limit=8" /*热门推荐接口地址*/,
        method: "get",
      })
        .then((res) => {
          //console.log("我拿到的数据：", res.data.result);
          this.commends=res.data.result;
        })
        .catch((err) => {
          console.log(err);
        });
    },
  },
      
  
}
</script>
<style lang="scss" scoped>
.wrap {
  display:flex;
  flex-direction:row;
  flex-wrap:wrap;
  justify-content:space-between;
  margin-top:20px;
  .sum{
     width:140px;
     height:210px;
     position:relative;
     margin-bottom:20px;
     margin-right:5px;
     margin-left:5px;
        img{
          width:140px;
          height:140px;
          }
        span{
          display:block;
          position:absolute;
          top:0px;
          left:0px;
          width:140px;
          height:140px;
          background:url('../assets/image/coverall.png');
          background-position:140px -380px;
        }
        
     
    .tit{
        display:block;
        font-size:14px;
        color:#000;
        margin-top:10px;
        width:140px;
        height:57px;
        text-align:left;
        text-decoration:none; 
      }
      .tit:hover{
        text-decoration:underline;
        cursor:point;
      }
      .play{
        background:url("../assets/image/coverall.png");
        background-position:0px -536px;
          text-align:left;
          height:30px;
          line-height:30px;
          width:140px;
          font-size:12px;
          color:#ccc;
          position:absolute;
          bottom:68px;
          left:0px;
          border:none;
          padding-left:10px;
          vertical-align:middle;
          .ear{
              display:inline-block;
              margin-top:1px;
              float:left;
              width:20px;
              height:20px;
              background:url("../assets/image/iconall.png");
              background-position:0px -16px;
          }
          a{
              display:inline-block;
              float:right;
              width:20px;
              height:29px;
              background:url("../assets/image/iconall.png");
              background-position:0px 7px;
          }
      }

  }
}
</style>
