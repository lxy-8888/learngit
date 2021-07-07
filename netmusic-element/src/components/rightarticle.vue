<template>
  <div>
    <div class="top">
      <p>登录网易云音乐，可以享受无限收藏的乐趣，并且无限同步到手机</p>
      <button type="button">用户登录</button>
    </div>
    <div class="down">
      <span>入驻歌手 <a href="#">查看全部></a></span>
      <el-divider></el-divider>
      <el-menu class="el-menu-vertical-demo" v-for="item in singer"  :key="item.id">
        <el-menu-item style="padding:0px;border:1px solid #e9e9e9" >
        <img  :src='item.img'></img>
         <div>
            <span>{{item.name}}</span>
            <p>{{item.des}}</p>
         </div>
       </el-menu-item>
    </el-menu>
      <el-row>
           <el-button type="info" plain> 申请成为网易音乐人</el-button>
  
     </el-row>
      <span>热门主播</span>
      <el-divider></el-divider>
       <el-menu class="el-menu-vertical-demo" v-for="item in anchor" :key="item.id">
        <el-menu-item style="padding:0px;margin-bottom:0px;height:40px" >
        <img style="width:40px;height:40px" :src='item.img' />
         <div style="width:172px;height:40px;line-height:40px;background:#fff">
            <span style="left:50px;height:20px;top:-4px">{{item.name}}</span>
            <p style="left:50px;width:166px;height:20px;top:24px">{{item.des}}</p>
         </div>
       </el-menu-item>
    </el-menu>
    </div>
  </div>
</template>
<script>
import axios from "../plugins/axios.js";
export default {
    data(){
        return{
            singer:[
              {id:10559,name:"张惠妹aMEI",img:"https://p2.music.126.net/rCsLFXha6SLis0tV7yZ5fA==/109951165588539704.jpg",des:"台湾歌手张惠妹"},
              {id:1160085,name:"Fine乐团",img:"https://p1.music.126.net/wDxCsT3YEYdNg-UZU_ZKeg==/109951166047225823.jpg",des:"独立音乐人"},
              {id:5345,name:"萬曉利",img:"https://p1.music.126.net/TiRAIiIihOgtBgYB6DZRXA==/109951162916034289.jpg",des:"民谣歌手，中国现代民谣的代表人物之一"},
              {id:6731,name:"音乐人赵雷",img:"https://p1.music.126.net/w_UWOls2uCkFN_U62788Xg==/18806046882229308.jpg",des:"民谣歌手"},
              {id:3669,name:"王三溥",img:"https://p1.music.126.net/NDsX060FnCtiDMZN-c_9Gw==/3438172872737957.jpg",des:"音乐人"}
            ],
             anchor:[
               {id:1,name:"陈立",des:"心理学家、美食家陈立教授",img:"http://p1.music.126.net/S7dd9GvTPwl5IHym8qF8VA==/109951164999332400.jpg"},
               {id:2,name:"刘维-Julius",des:"歌手、播客节目《维维道来》主理人",img:"http://p1.music.126.net/S7dd9GvTPwl5IHym8qF8VA==/109951164999332400.jpg"},
               {id:3,name:"莫非定律MoreFeel",des:"男女双人全创作独立乐团",img:"http://p1.music.126.net/S7dd9GvTPwl5IHym8qF8VA==/109951164999332400.jpg"},
               {id:4,name:"碎嘴许美达",des:"脱口秀网络红人",img:"http://p1.music.126.net/S7dd9GvTPwl5IHym8qF8VA==/109951164999332400.jpg"},
               {id:5,name:"银临Rachel",des:"古风音乐人",img:"http://p1.music.126.net/S7dd9GvTPwl5IHym8qF8VA==/109951164999332400.jpg"}
             ]

        }
    },
    created(){
        this.getsingers()
    },
    methods: {
        getsingers(){
            axios({
                url:"/dj/radio/hot?cateId=8",
                methods:"get"
            }) .then((res) => {
           // console.log(res);
        })
        .catch((error) => {
          console.log(error);
        });
        }
    },
    


};
</script>
<style lang="scss" scoped>
.top {
  width: 100%;
  height: 120px;
  background:url("../assets/image/index.png");
  background-position:2px 941px;
  padding-top: 20px;
  
  p {
    display: block;
    height: 44px;
    width: 80%;
    margin: 12px auto;
    text-align: left;
    color: #666;
    font-size: 12px;
    line-height: 22px;
  }
  button {
    border: none;
    border-radius: 8%;
    margin-bottom: 20px;
    width: 100px;
    height: 31px;
    color: #fff;
    font-size: 12px;
    margin: 0 auto;
    line-height: 31px;
    background-color: #cd0e15;
  }
}
.down {
  width: 85%;
  margin: 20px auto;
  height: 100%;
  span {
    width: 100%;
    display: inline-block;
    color: #333;
    font-weight: bold;
    font-size: 12px;
    position:relative;
    text-align:left;
    a {
      text-decoration: none;
      display: inline-block;
     position:absolute;
     right:0px;
     top:0px;
      color: #666;
      font-weight: normal;
    }
  }
  .el-divider--horizontal{
      margin:6px 0;
  }
  .el-menu {
    border-right:none;
    list-style: none;
    position: relative;
    margin: 0;
    padding-left: 0;
    
    .el-menu-item{
       height:65px;
       margin-top:10px;
       margin-bottom:10px;
      
       
        img{
            float:left;
            width:62px;
            height:62px;
            line-height:62px;
            float:left;
        }
        div{
            background:#fafafa;
            float:left;
            height:62px;
            width:70%;
          
            font-size:14px;
            color:#666;
             span{
            font-weight:bold;
           font-size:14px;
            width:120px;
            height:30px;
            line-height:30px;
            display:inline-block;
            position:absolute;
            left:80px;
            top:5px;
            text-align:left;     
        }
        span:hover{
          text-decoration:underline;
          cursor:point;
        }
        p{
           font-size:12px;
            text-align:left;
           height:20px;
           line-height:20px;
           width:120px;
          position:absolute;
          top:35px;
          left:80px;
          overflow:hidden;
          text-overflow:ellipsis;
        }
        }
       
    }

    }
    .el-row{
        margin-bottom:20px;
        width:100%;
        margin-top:15px;
        .el-button {
         height:30px;
         width:100%;
        font-size:12px;
        font-weight:bold;
        color: #333;
        line-height:6px;
          }
          .el-button:hover{
              background-color:#f4f4f5;
          }
    }
}
</style>
