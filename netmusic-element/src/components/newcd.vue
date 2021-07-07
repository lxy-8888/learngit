<template>
  <div class="max">
    <div class="bbox">
      <span class="circle"></span>
      <span class="start">新碟上架</span>
      <span class="arrow">更多</span>
    </div>
 <el-carousel :autoplay="false" indicator-position="none" arrow="never" height="212px"  ref="img">
    <el-carousel-item v-for="(item,index) in news" :key="index" >
    
    <div class="fixed">
       <div class="pic">
      <span class="left-arrow" @click="prev"></span>
      <div class="pwrap" v-for="(item1, index1) in item" :key="index1">
        <span></span>
        <img :src="item1.blurPicUrl" alt="" />
        <p class="title">{{ item1.name }}</p>
        <p class="detail">{{ item1.artist.name }}</p>
      </div>
      <span class="right-arrow" @click="next"></span>
    </div>
    </div>
   
  
    </el-carousel-item>
  </el-carousel>

  </div>
</template>
<script>
import axios from "../plugins/axios.js";
export default {
  components: {},
  data() {
    return {
      news: {
        arr1:"",
        arr2:""
      },
    };
  },
  created() {
    this.getnewcd();
  },
  
  methods: {
    prev(){
     this.$refs.img.prev();
    },
    next(){
      this.$refs.img.next();
    }
  ,
    getnewcd() {
      axios({
        url: "/album/newest",
        method: "get",
      })
        .then((res) => {
        //  console.log("数据：", res.data.albums);
          let arrnew=res.data.albums;
          this.news.arr1 = arrnew.slice(0,5);
          this.news.arr2=arrnew.slice(5,10);
         // this.news=res.data.albums;
        })
        .catch((err) => {
          console.log(err);
        });
    },
  },
};
</script>
<style lang="scss" scoped>
.max {
  //overflow: hidden;
  
  .bbox {
    width: 100%;
    height: 35px;
    line-height: 35px;
    text-align: left;
    border-bottom: 2px solid #c10d0c;
    font-size: 12px;
    color: #666;
    .el-carousel__container {
    position: relative;
    overflow: hidden;
}
    
    .circle {
      display: inline-block;
      margin-right: 10px;
      width: 20px;
      height: 20px;
      background: url("../assets/image/index.png");
      background-position: 183px 305px;
    }
    .arrow {
      display: inline-block;
      margin-left: 540px;
      width: 35px;
      height: 20px;
      background: url("../assets/image/index.png");
      background-position: 25px 700px;
    }
    .start {
      line-height: 35px;
      font-size: 20px;
      color: #333;
      margin-right: 25px;
    }
  }
  .fixed{
    overflow:hidden;
    
  }
  .pic {
    position: relative;
    margin-top: 20px;
    padding-left: 10px;
    padding-right: 10px;
    border: 1px solid #d3d3d3;
    height: 179px;
    background-color: #f5f5f5;
    display: flex;
    flex-direction: row;
    //flex-wrap: wrap;
    justify-content: space-around;

    .left-arrow {
      position: absolute;
      top: 67px;
      left: 0px;
      display: block;
      width: 20px;
      height: 20px;
      background: url("../assets/image/index.png");
      background-position: 571px 387px;
    }
   
    .left-arrow:hover {
      cursor: pointer;
    }
    .right-arrow:hover {
      cursor: pointer;
    }
    .right-arrow {
      top: 60px;
      right: 0px;
      position: absolute;
      display: block;
      width: 20px;
      height: 20px;
      background: url("../assets/image/index.png");
      background-position: 522px 392px;
    }
    
   .pwrap:hover {
      cursor: pointer;
    }
    .pwrap {
      width: 118px;
      height: 100px;
      margin: 20px 5px 40px 5px;
      text-align: left;
      position: relative;

      img {
        width: 100px;
        height: 100px;
      }
      span {
        display: block;
        position: absolute;
        top: 0px;
        left: 0px;
        width: 118px;
        height: 100px;
        background: url("../assets/image/coverall.png");
        background-position: -380px 925px;
      }
      .detail {
        margin-top: 3px;
        overflow: hidden;
        text-overflow: ellipsis;
        white-space: nowrap;
        font-size: 12px;
        color: #666;
      }
      .title {
        margin-top: 3px;
        overflow: hidden;
        text-overflow: ellipsis;
        white-space: nowrap;
        font-size: 12px;
        color: #000;
      }
      .title:hover{
        text-decoration:underline;
        cursor:pointer;
      }
    }
    
   
  }
}
</style>
