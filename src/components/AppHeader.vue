<template>
  <header class="header-register">
    <div class="nav-hide">
      <i class="fa fa-chevron-left arrow"></i>
    </div>
    <div @click="goHome" class="khu-logo"><img style="pointer-events:none;" src="khu-logo.png" /></div>
    <div class="timmer">
         <div class="time">
      <div class="timerRemain">{{min}}:{{sec}}</div>
      <button @click="extendTime" class="extend-btn" type="button">연장하기</button>
         </div>
      <div class="btn-lang" id="lang">ENG</div>
      <div @click="goHome" class="home" title="Home">
        <img style="pointer-events:none;" class="home-img" src="home.png" />
      </div>
      <div class="logout-btn" title="Logout">
        <i class="fa fa-unlock-alt lock"></i>
      </div>
    </div>
  </header>
</template>

<script>
//장시간 사용이 없어서 자동로그아웃 됩니다!. 
export default {
  name: "app-header",
  props: ["massage","leftTime"],
  data(){
    return{
      totalSec : 60*10,
      timer: null
    }
  },
  created(){
    this.timer = setInterval(()=>{
      this.totalSec-- 
    },1000);
  },
  watch :{
    totalSec(){
      if(this.totalSec==0){
        clearInterval(this.timer);
        this.$emit('timeOver')
      }
    },
  },
  computed: {
      min () {
      const minute = parseInt(this.totalSec/60); 
      return minute < 10 ? "0"+ minute.toString() : minute
    },
     sec () {
      const second = parseInt(this.totalSec%60); 
      return  second < 10 ? "0"+ second.toString() : second
    },
  },
  methods:{
    extendTime(){
      this.totalSec = 60*10;
    },
    goHome(){
      this.$emit('home'); 
    }
  }
};
</script>

<style>
.header-register{
    min-width: 1260px;
    width: calc(100vw - 120px);
    background-color: white;
    border: 1px solid rgb(236, 236, 236);
    height: 60px;
    display: flex;
    align-items:center;
    justify-content: space-between;
    z-index: 3;
    font-size: 16px;
}
.header-register .nav-hide{
      width: 17px;
      background-color: #F4F4F4;
      height: inherit;
      font-weight: lighter;
      border: 1px solid rgb(236, 236, 236);
  }
  .header-register .arrow{
      color : rgb(128, 128, 128);
      padding :21px 0 0 2px;
      height: 20px;
      font-size: 12px;
  }
  .header-register .khu-logo{
      padding-left: 12px;
  }
  /* 타이머 부분 */
.timmer{
    left:0;
    font-size: 16px;
    margin-left: auto;
    height: inherit;
    display: flex;
    justify-content: flex-start;
    align-items: center;
    text-align: center;
  }
 .timmer div{
    font-size: 16px;
    height: inherit;
    line-height: 55px;
  }
  .timmer .time{
      display: flex;
  }
  .timmer .time .timerRemain{
      font-weight: 400;
      color: #e04616;
      text-align: center;
  }
  .timmer .time .timerRemain::before{
      content:"\f017";
      font-family: "fontawesome";
      color:rgb(128, 128, 128);
      font-weight: lighter;
      opacity: 0.5;
      margin-right: 3px;
  }
  .timmer .time .extend-btn{
      margin:15px 0 0 8px;
      border: 1px solid #ddd;
      border-radius: 2px;
      font-size: 12px;
      width: 60px;
      height: 30px;
      line-height: 20px;
      margin-right: 20px;
  }
  /*  */
  .timmer .btn-lang,.home,.logout-btn{
      margin: 0 15px;
      color:rgb(128, 128, 128);
  }
  .timmer .btn-lang{
    width: 46px;
    font-weight: 700;
    position:relative;
     
  }
  .timmer .btn-lang::after{
      content: '';
      width: 1px;
      height: 20px;
      background-color: #ddd;
      position:absolute;
      margin-top: 10px;
      right: -10px;
      top: 8px;
  }
  /* 홈 이미지 */
  .timmer .home{
      width: 38px;
      color: black;
      z-index: 1001;
      position:relative;
  }
  .timmer .home-img{
      margin: 14px 10px 0 0 ;
      width: 27px;
      height: 27px;
      object-fit: contain;
      filter: opacity(.5) drop-shadow(0 0 0 rgb(236, 236, 236));
  }
  .timmer .home::after{
      content: '';
      width: 1px;
      height: 20px;
      background-color: #ddd;
      position:absolute;
      margin-top: 10px;
      right: -10px;
      top: 8px;
  }
  .timmer .logout-btn{
      width: 32px;
  }
  .timmer .logout-btn .lock{
    font-size: 17px;
    color: #7e7e7e;
  }
</style>