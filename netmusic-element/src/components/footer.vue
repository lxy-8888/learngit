<template>
  <div class="wrap">
    <span><a href="#">服务条款</a></span>
    <el-divider direction="vertical"></el-divider>
    <span><a href="#">隐私政策</a></span>
    <el-divider direction="vertical"></el-divider>
    <span><a href="#">儿童隐私政策</a></span>
    <el-divider direction="vertical"></el-divider>
    <span><a href="#">版权投诉指引</a></span>
    <el-divider direction="vertical"></el-divider>
    <span><a href="#">意见反馈</a></span>
    <br />
    <span>网易公司版权所有©1997-2021</span>
    <span
      >杭州乐读科技有限公司运营：<a href="#" style="color: #666"
        >浙网文[2021] 1186-054号</a
      ></span
    ><br />
    <span
      >违法和不良信息举报电话：0571-89853516 举报邮箱：<a href="#" style="color: #666"
        >ncm5990@163.com</a
      ></span
    ><br />
    <a href="#" style="color: #666; text-decoration: none"
      >粤B2-20090191-18 工业和信息化部备案管理系统网站<span class="icon"></span>浙公网安备
      33010902002564号
      <div class="iconss">
        <ul>
          <li></li>
<span>Amped Studio</span>
          <li></li>
<span>用户认证</span>
          <li></li>
<span>独立音乐人</span>
          <li></li>
<span>赞赏</span>
          <li></li>
          <span>视频奖励</span>
        </ul>
      </div>
    </a>
  </div>
</template>
<script>
export default {};
</script>
<style lang="scss" scoped>
.wrap {
  width: 1025px;
  height: 172px;
  margin: 0 auto 0 250px;
  font-size: 12px;
  line-height: 24px;
  color: #666;
  padding-top: 20px;
  text-align: left;
  position: relative;
 
  .iconss {
    position: absolute;
    right: 0px;
    top: 0px;
    width: 450px;
    height: 172px;
   
    margin-top: 10px;
    ul {  
      height: 150px;
      list-style: none;
      position:relative;
       :nth-child(9) {
        background-position: 50px 398px;  
         top:20px;
        left:362px;
      }
      :nth-child(7) {
        background-position: 50px 442px;  
        top:20px;
        left:273px;
      }
      :nth-child(5) {
        background-position: -199px -474px; 
         top:20px;
        left:192px; 
      }
      :nth-child(3) {
        background-position: 50px 88px;  
        top:20px;
        left:100px;
      }
      :nth-child(1) {
        background-position: 50px -83px; 
        top:20px;
        left:15px; 
      }
      li{
        position:absolute;
        display: inline-block;
        margin-right:10px;
        width: 50px;
        height: 50px;
        background-image: url("../assets/image/foot_enter_new.png");
        background-size:100px 480px;
      }
      span{
        position:absolute;
      }
      :nth-child(2){
        top:70px;
        left:12px;
        
      }
       :nth-child(4){
        top:70px;
        left:108px;
        
      }
       :nth-child(6){
         top:70px;
        left:188px;
        
      }
       :nth-child(8){
         top:70px;
        left:293px;
        
      }
       :nth-child(10){
        top:70px;
        left:368px;
        
      }
    }
  }
  .el-divider {
    width: 2px;
  }
  .icon {
    display: inline-block;
    width: 14px;
    height: 14px;
    background-image: url("../assets/image/police.png");
    background-size: cover;
    margin: auto 3px auto 8px;
  }
  span {
    a {
      color: #999;
      text-decoration: none;
    }
  }
}
</style>
