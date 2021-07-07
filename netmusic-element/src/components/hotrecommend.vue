<template>
  <div class="max">
    <div class="bbox">
      <span class="circle"></span>
      <span class="start">热门推荐</span>
      <span class="hoverspan">华语</span>
      <el-divider direction="vertical" content-position="left"></el-divider>
      <span class="hoverspan">流行</span>
      <el-divider direction="vertical" content-position="left"></el-divider>
      <span class="hoverspan">摇滚</span>
      <el-divider direction="vertical" content-position="left"></el-divider>
      <span class="hoverspan">民谣</span>
      <el-divider direction="vertical" content-position="left"></el-divider>
      <span class="hoverspan">电子</span>
      <span class="arrow">更多</span>
    </div>
    <div class="pic">
      <Peritem />
    </div>
  </div>
</template>
<script>
import Peritem from "./playitem.vue";
export default {
  components: {
    Peritem,
  },
  data() {
    return {
      commends: "",
    };
  },
  methods:{

      
  }
};
</script>
<style lang="scss" scoped>
.max {
  .bbox {
    width: 100%;
    height: 35px;
    line-height: 35px;
    text-align: left;
    border-bottom: 2px solid #c10d0c;
    font-size: 12px;
    color: #666;
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
      margin-left: 350px;
      width: 35px;
      height: 20px;
      background: url("../assets/image/index.png");
      background-position: 25px 700px;
    }
    .arrow:hover{
      text-decoration:underline;
      cursor:pointer;
    }
    .hoverspan:hover{
      text-decoration:underline;
      cursor:pointer;
    }
    .start {
      line-height: 35px;
      font-size: 20px;
      color: #333;
      margin-right: 25px;
    }
    .pic {
    }
  }
}
</style>
