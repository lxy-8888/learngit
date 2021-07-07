<template>
  <div class="home">
    <a href="#" class="top-icon"></a>
    <el-container>
      <el-header height="70px">
        <h1 class="logo"></h1>
        <el-menu
          :default-active="this.$route.path"
          class="ulbox"
          mode="horizontal"
          @select="handleSelect"
          background-color="#242424"
          text-color="#ccc"
          active-text-color="#fff"
        >
          <el-menu-item
            class="hoverbox"
            index="1"
            v-for="(item, i) in navList"
            :key="i"
            :index="item.name"
          >
            <span> {{ item.navItem }} </span>
          </el-menu-item>
        </el-menu>
        <span class="hot"></span>
        <div class="input" >
         <input  placeholder="音乐/视频/电台/用户"></input>
         <span class="searchicon"></span>
        </div>
        <span class="create">创作者中心</span>
        <a href="#" class="login">登录</a>
        
       
      </el-header>
     
      <el-main class="mainbox"> <Banner />
         <div class="middlebox">
             <el-row class="rowbox">
           <el-col :span="18"  ><div class="left">
           <Hot/>
           <New/>
           <List/>
           </div></el-col>
           <el-col :span="6"  > <div class="right"><Article/></div></el-col>
             </el-row>
        </div> 
      </el-main>
      <el-footer height="172px"><Footer/></el-footer>
    </el-container>
  </div>
</template>

<script>
// @ is an alias to /src
import axios from "@/plugins/axios.js"; /*引入封装的axios*/
import Banner from "../components/banner.vue";
import Hot from '../components/hotrecommend.vue';
import New from '../components/newcd.vue';
import List from '../components/blist.vue';
import Footer from '../components/footer.vue';
import Article from '../components/rightarticle.vue';
export default {
  name: "Home",
  components: { Banner,Hot,New,List,Footer,Article},
  data() {
    return {
      navList: [
        { name: "/Home.vue", navItem: "发现音乐" },
        { name: "/Mymusic.vue", navItem: "我的音乐" },
        { name: "/Friend.vue", navItem: "朋友" },
        { name: "/Shop.vue", navItem: "商城" },
        { name: "/Musician.vue", navItem: "音乐人" },
        { name: "/Download.vue", navItem: "下载客户端" },
      ],
    };
  },
  methods: {
    handleSelect(key, keyPath) {},
  }
}
</script>
<style lang="scss" scoped>
.home {
 
  height: 100vh;
  position:relative;
  .top-icon{
    display:block;
    background:url("../assets/image/sprite.png");
    background-position:216px -47px;
    position: absolute;
    left: 52%;
    margin-left: 500px;
    top: 1676px;
    width: 49px;
    height: 44px;
    z-index:2;
    
  }
}
 

.el-header {
  position: relative;
  height: 70px;
  width: 100%;
  background-color: #242424;
  color: #ccc;
  text-align: center;
  line-height: 70px;
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  align-items:center;
  .hot {
    position: absolute;
    right: 557px;
    width: 40px;
    height: 40px;
    background: url("../assets/image/topbar.png");
    background-position: 55px 5px;
  } 
  .input{
    margin-left:30px;
    position:relative;
    border:none;
    input{
    color:#9b9b9b;
    font-size:12px;
    outline:none;
    border:1px solid #999;
    box-sizing: border-box;
    background-color:#fff;
    line-height: 32px;
      width:158px;
      height:32px;
      padding-left:30px;
      border-radius:32px;
    }
    .searchicon{
      position:absolute;
      display:block;
      left:3px;
      bottom:10px;
      width:32px;
      height:32px;
      background:url("../assets/image/topbar.png");
      background-position:0px 324px;
     
    }
  }
  .create{
    line-height:32px;
    font-size:12px;
    width:90px;
    height:32px;
    color:#fff;
    display:inline-block;
    border-radius:20px;
    border:1px solid #4F4F4F;
    margin-left:15px;
    margin-right:15px;
    background-color:transparent;
  }
  .login{
     font-size:12px;
     text-decoration: none;
     color:#787878;
  }
  
  
  h1 {
    margin-left: 200px;
    width: 176px;
    height: 69px;
    background: url("../assets/image/topbar.png");
  }
  .ulbox {
    background-color: #242424;
    border: none;
    width: 600px;
    height: 70px;
    line-height: 70px;
    .hoverbox {
      background-color: #242424;
      border: none;
      height: 70px;
      line-height: 70px;
      padding: 0px;
      overflow: hidden;
      span {
        display: inline-block;
        width: 96px;
        line-height: 70px;
      }
      span:hover {
        background-color: #000000;
      }
    }
  }
}

.el-footer {
  position: relative;
  height: 172px;
  overflow: hidden;
  border-top: 1px solid #d3d3d3;
  background: #f2f2f2;
}
.el-main {
  background-color: #f5f5f5;
  color: #333;
  text-align: center;
  flex-grow: 1;
  padding: 0px;
  
  .middlebox{
    background-color:#fff;
    width:1003px;
    margin:0 auto;
  //  margin-left:271px;
    border-left:1px solid #d3d3d3;
    border-right:1px solid #d3d3d3;
    padding:0px 0px 0 20px;
    .el-row {
     height:100%;
       
    }
     .el-col:first-child{
       width:74.8%;
       height:100%;
       padding-right:20px;
       border-right:1px solid #d3d3d3;
       padding-top:20px;
     }
     .el-col:last-child{
       width:25.2%;
       height:900px;
       div{
         
         width:100%;
         height:100%;
       }
     }
   
    
    
      
  }
      
 
  
}

body > .el-container {
  margin-bottom: 40px;
}
</style>
