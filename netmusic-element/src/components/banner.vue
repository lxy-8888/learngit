<template>
  <div class="temp">
    <Tabs/>
    <div class="lf">
      <el-carousel
        :interval="5000"
        arrow="always"
        class="my-el-carousel"
        width="730px"
        height="285px"
      >
        <el-carousel-item class="my-item" v-for="(item, index) in pics" :key="index">
          <img :src="item.imageUrl" />
        </el-carousel-item>
      </el-carousel>
      <div class="right">
      <a href="#">下载客户端</a>
      <p>PC 安卓 iPhone WP iPad Mac 六大客户端</p>
      </div>
    </div>
    
  </div>
</template>
<script>
import axios from "@/plugins/axios.js"; /*引入封装的axios*/
import Tabs from "./topred.vue"
import Swiper from 'swiper';
import 'swiper/swiper-bundle.css';
export default {
  components: {
      Tabs
  },
  data() {
    return {
      pics: {},
    };
  },
  async created() {
    this.init();
  },

  methods: {
    async init() {
      //这边是引入了axios然后使用的get请求的一个音乐列表接口
      //这边url随大家更改了
      let data = await axios.get("/banner"); //使用await ，data会等到异步请求的结果回来后才进行赋值
      //以下就是这边对请求的一个处理，看接口了
      if (data.status == 200) {
        //200: '服务器成功返回请求的数据
        this.pics = data.data.banners;
        
      }
    },
  },
};
</script>
<style lang="scss" scoped>
.temp {
  width: 100%;
  height: 320px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
 
  .lf {
    
    margin: 0 auto;
    width: 1200px;
    height: 285px;
    display: flex;
    flex-direction: row;
    justify-content: flex-start;
    .my-el-carousel {
      width: 1200px;
      height: 100%;
      margin: 0px;
      padding: 0px;
      
      .my-item {
        width:946px;
        vertical-align: middle;
        text-align: center;
        display: table-cell;

        img {
          max-width: 100%;
          max-height: 100%;
        }
      }
    }
    .right {
      margin-left:-342px;
      width: 255px;
      background:url("../assets/image/download.png");
      text-align:center;
      position:relative;
     
        a{
        display:block;
        width:215px;
        height:56px;
        position:absolute;
        left:19px;
        bottom:44px;
        background:transparent;
        border:0px;
        text-indent:-99999px;
        }
       
  
      p{
        color:#8d8d8d;
        font-size:12px;
        position:absolute;
        left:15px;
        bottom:15px;
      }
    }
  }
}
</style>
