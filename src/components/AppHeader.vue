<template>
  <header>
    <div class="nav-hide">
      <i class="fa fa-chevron-left arrow"></i>
    </div>
    <div @click="goHome" class="khu-logo"><img style="pointer-events:none;" src="khu-logo.png" /></div>
    <div class="timmer">
      <div class="timerRemain">{{min}}:{{sec}}</div>
      <button @click="extendTime" class="extend-btn" type="button">연장하기</button>
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
header {
  height: 80px;
  background-color: black;
  width: 100vw;
  color: white;
}

header{
    background-color: white;
    border: 1px solid rgb(236, 236, 236);
    height: 60px;
    display: flex;
    align-items: center;
    position:fixed;
    width: calc(100vw - 120px);
    z-index: 3;
    font-size: 16px;
}
.nav-hide{
    width: 17px;
    background-color: #F4F4F4;
    height: inherit;
    font-weight: lighter;
    border: 1px solid rgb(236, 236, 236);
}
.arrow{
    color : rgb(128, 128, 128);
    padding :21px 0 0 2px;
    height: 20px;
    font-size: 12px;
}
.khu-logo{
    padding-left: 12px;
    width: 288px;
}
/* 타이머 부분 */

.timmer{
   font-size: 16px;
    margin-left: auto;
    width: 357px;
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
.timerRemain{
    font-weight: 400;
    color: #e04616;
    width: 76px;
    text-align: center;
}
.timerRemain::before{
    content:"\f017";
    font-family: "fontawesome";
    color:rgb(128, 128, 128);
    font-weight: lighter;
    opacity: 0.5;
    margin-right: 3px;

}
.extend-btn{
    border: 1px solid #ddd;
    border-radius: 2px;
    font-size: 12px;
    width: 60px;
    height: 30px;
    line-height: 20px;
    margin-right: 20px;
}
.btn-lang,.home,.logout-btn{
    margin: 0 15px;
    color:rgb(128, 128, 128);
}
.btn-lang{
  width: 46px;
  font-weight: 700;
  position:relative;
   
}
.btn-lang::after{
    content: '';
    width: 1px;
    height: 20px;
    background-color: #ddd;
    position:absolute;
    margin-top: 10px;
    right: -10px;
    top: 8px;
}
.home{
    width: 38px;
    color: black;
    z-index: 1001;
    position:relative;
}
.home-img{
    margin: 14px 10px 0 0 ;
    width: 27px;
    height: 27px;
    object-fit: contain;
    -webkit-filter: opacity(.2) drop-shadow(0 0 0 gray);
    filter: opacity(.5) drop-shadow(0 0 0 rgb(236, 236, 236));
    
}
.home::after{
    content: '';
    width: 1px;
    height: 20px;
    background-color: #ddd;
    position:absolute;
    margin-top: 10px;
    right: -10px;
    top: 8px;
}
.logout-btn{
    width: 32px;
}
.logout-btn .lock{
  font-size: 17px;
  color: #7e7e7e;
}

</style>