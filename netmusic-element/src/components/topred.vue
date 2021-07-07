<template>
  <div class="topred">
  <ul class="ulbox">
    <li class="libox" :class="item.isShow ?'active':''" v-for="(item,index) in tittle" :key="index">{{item.navItem}}</li>
    <span class="ricon"></span>
  </ul>
  </div>
</template>
<script>
export default {
  data() {
    return {
      active: "0",
      tittle: [
        { name: "/Home.vue", isShow:true,navItem: "推荐" },
        { name: "/Mymusic.vue",  isShow:false,navItem: "排行榜" },
        { name: "/Friend.vue", isShow:false, navItem: "歌单" },
        { name: "/Shop.vue",  isShow:false,navItem: "主播电台" },
        { name: "/Musician.vue", isShow:false, navItem: "歌手" },
        { name: "/Download.vue",  isShow:false,navItem: "新碟上架" },
      ],
    };
  },
  methods: {
    handleClick(tab, event) {
      console.log(tab, event);
    },
  },
};
</script>
<style lang="scss" scoped>
.topred {
  width:100%;
  height: 35px;
  box-sizing: border-box;
  background-color: #c20c0c;
  border-bottom: 1px solid #a40011;
  text-align:center;
  .ulbox{
    text-align:left;
    width:715px;
    height:35px;
    margin:0 auto;
    line-height:35px;
    position:relative;
    .ricon{
      position:absolute;
      top:10px;
      left:225px;
      width:10px;
      height:10px;
      background:url('../assets/image/white-r-icon@3x.png');
      background-size:cover;
    }
    .libox{
      margin-right:30px;
      list-style:none;
      display:inline-block;
      width:60px;
      height:20px;
      font-size:12px;
      color:#fff;
      text-align:center;
      line-height:20px;
    }
    .libox:hover{
      background-color:#9B0909;
      border-radius:20px;
   }
     .active{
      background-color:#9B0909;
      border-radius:20px;
    }
     
    

  }
}
</style>
