<template>
  <div class="main">
    <div class="header">
      <div class="icon"><img src="../../static/img/icon.png"/></div>
      <div class="search">
          <input placeholder="请输入内容" v-model="seacrhData" class="input-with-select"/>
        <div class="searchbtn"><img src="../../static/img/search.png"/></div>
      </div>
    </div>
    <div class="contain">
      <div class="frist" v-if="avtivemun === 0">
        <div class="bg bgone"></div>
        <div class="frist-left">
          <div>欢迎来到蓝慕靖歌网站</div>
          <div>我是大龙湖畔</div>
          <div>是一个爱音乐、爱折腾、爱生活</div>
          <div>会找影视资源的好人</div>
          <!-- <el-button type="primary" style="margin-top: 5px;background: #c2435a;border: none">主要按钮</el-button> -->
        </div>
        <!-- <div class="frist-rigth">
          <img src="../../static/img/people.jpg"/>
        </div> -->
      </div>
      <div class="frist" v-if="avtivemun === 1">
        <div class="bgtwo bg"></div>
        <div class="content">
          <div>观点与分享</div>
          <div>记录生活点滴，分享人生喜乐！</div>
          <!-- <el-button type="primary" style="margin-top: 5px;background: #c2435a;border: none">主要按钮</el-button> -->
        </div>
      </div>
      <div class="frist" v-if="avtivemun === 2">
        <div class="bgthree bg"></div>
        <div class="content">
          <div>影视与感官</div>
          <div>观看生活影片，感受欢天喜地！</div>
          <!-- <el-button type="primary" style="margin-top: 5px;background: #c2435a;border: none">主要按钮</el-button> -->
        </div>
      </div>
      <div class="frist" v-if="avtivemun === 3">
        <div class="bgfour bg"></div>
        <div class="content">
          <div>志趣相投</div>
          <div> 我们都一样热爱生活，记录生活，享受生活！</div>
          <!-- <el-button type="primary" style="margin-top: 5px;background: #c2435a;border: none">主要按钮</el-button> -->
        </div>
      </div>
      <div class="frist" v-if="avtivemun === 4">
        <div class="bgfive bg"></div>
        <div class="content">
          <div>说走就走</div>
          <div> 生活不止眼前的苟且，还有诗和远方的田野！</div>
          <!-- <el-button type="primary" style="margin-top: 5px;background: #c2435a;border: none">主要按钮</el-button> -->
        </div>
      </div>
      <div class="menu-box">
        <div class="menu">
          <div :class="avtivemun==index?'active':''" v-for="(item,index) in menu" :key="index" class="menu-item" @click="changetab(index)">
            <i :class="item.icon"></i>
            <div style="margin-top: 2px">{{item.name}}</div>
          </div>
        </div>

      </div>
    </div>
    <div class="footer">
      © 2022 蓝慕靖歌 · 
      <a @click="toBeiAn" >
        <span class="footer-beian">桂ICP备2022001203号-1</span>
      </a>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      url: 'https://beian.miit.gov.cn/',
      timer:undefined,
      seacrhData:undefined,
      avtivemun:0,
      menu:[{
        name:'简介',
        icon:'el-icon-user-solid',
        router:''
      },{
        name:'随记',
        icon:'el-icon-platform-eleme',
        router:''
      },{
        name:'影视',
        icon:'el-icon-video-camera-solid',
        router:''
      },{
        name:'圈子',
        icon:'el-icon-help',
        router:''
      },{
        name:'旅行',
        icon:'el-icon-s-promotion',
        router:''
      },]
    }
  },
  methods:{
    changetab(index){
      this.avtivemun = index
    },
    toBeiAn(){
      window.open(this.url, "_blank");
    }
  },
  mounted() {
    var _this = this
    this.timer = setInterval(function(){
      _this.avtivemun  = _this.avtivemun + 1
      if(_this.avtivemun === 5){
        _this.avtivemun = 0
      }
    },3000);
  },
  destroyed() {
    clear(this.timer)
  },
  created() {
  },
}
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .main{
    height: 100vh;
    width: 100%;
  }
  .header{
    width: 100%;
    height: 60px;
    background: #161618;
  }
  .icon{
    width: 40px;
    height: 40px;
    float: left;
    margin-top: 10px;
    margin-left: 10px;
  }
  .icon img{
    width: 100%;
    height: 100%;
  }
  .search{
    float: right;
    margin-top: 15px;
    margin-right: 10px;
    display: flex;
  }
  .input-with-select{
    width: 120px;
    height: 25px;
    border-top-left-radius: 7px;
    border-bottom-left-radius: 7px;
    border: none;
    background: #343434;
    padding-left: 10px;
  }
  .searchbtn{
    width: 30px;
    height: 27px;
    /*margin-top: 15px;*/
    background: #7c7c7c;
    border-top-right-radius: 7px;
    border-bottom-right-radius: 7px;
    line-height: 27px;
  }
  .searchbtn img{
    width: 16px;
    height: 16px;
    margin-left: 5px;
  }
  .contain{
    width: 100%;
    height: calc(100vh - 90px);
  }
  .frist{
    width: 100%;
    height:100%;
    position: relative;
  }
  .menu-box{
    position: absolute;
    bottom: 30px;
    width: 100%;
    height: 80px;
    background: rgba(0,0,0,.5);
    text-align: center;
    display: flex;
    justify-content: center;
  }
  .menu{
    display: flex;
  }
  .menu-item{
    width: 80px;
    color: #fff;
    padding-top: 15px;
    cursor: pointer;
  }
  .active{
    background: #fff;
    color: #000;
    border-top:2px solid #c2435a;
  }
  .bg{
    width: 100%;
    height:100%;
    /*background-size: contain;*/
    -webkit-filter: blur(5px);
    -moz-filter: blur(5px);
    -o-filter: blur(5px);
    -ms-filter: blur(5px);
    filter: blur(5px);
  }
  .bgone{
    background: url("../../static/img/pic1.jpg");
    background-size: 100%;
    background-position: 50% 0;
  }
  .bgtwo{
    background: url("../../static/img/pic2.jpg");
    background-size: 100%;
    background-position: 50% 0;
  }
  .bgthree{
    background: url("../../static/img/pic5.jpg");
    background-size: 100%;
    background-position: 50% 0;
  }
  .bgfour{
    background: url("../../static/img/pic4.jpg");
    background-size: 100%;
    background-position: 50% 0;
  }
  .bgfive{
    background: url("../../static/img/pic3.jpg");
    background-size: 100%;
    background-position: 50% 0;
  }
  .content{
    position: absolute;
    text-align: center;
    width:100%;
    top:0;
    left: 0;
    font-size: 30px;
    color: #ffffff;
    padding-top:15%;
    line-height: 50px;
  }
  .frist-left{
    position: absolute;
    text-align: center;
    width:60%;
    top:0;
    left: 0;
    line-height: 50px;
    font-size: 30px;
    color: #ffffff;
    padding-top:15%;
    padding-left:5%;
  }
  .frist-rigth{
    position: absolute;
    text-align: left;
    width:40%;
    top:0;
    left: 60%;
  }
  .frist-rigth img{
    width: 300px;
    padding-top:29%;
  }
  .footer{
    box-sizing: border-box;
    width: 100%;
    height: 30px;
    line-height: 30px;
    text-align: center;
    background: #161618;
    color: #eeee;
    font-size: 14px;
  }
  .footer-beian{
    width: 80px;
    color: #fff;
    padding-top: 15px;
    cursor: pointer;
  }
</style>
