<template>
  <header>
    <div class="nav-hide">
      <i class="fa fa-chevron-left arrow"></i>
    </div>
    <div class="khu-logo"><img src="khu-logo.png" /></div>
    <div class="timmer">
      <div class="timerRemain">00:01</div>
      <button class="extend-btn" type="button">연장하기</button>
      <div class="btn-lang" id="lang">ENG</div>
      <div class="home" title="Home">
        <img class="home-img" src="home.png" />
      </div>
      <div class="logout-btn" title="Logout">
        <i class="fa fa-unlock-alt"></i>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: "app-header",
  props: ["massage"],
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
    z-index: 1001;
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
    margin-left: auto;
    width: 357px;
    height: inherit;
    display: flex;
    justify-content: flex-start;
    align-items: center;
    text-align: center;
}
.timmer div{
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

</style>