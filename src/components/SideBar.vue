<template>
  <section class="re-sidebar">
    <div class="re-nav">
      <div class="re-myinfo"> 
        <a style="font-weight: 400; font-size:16px">KYUNG HEE</a>
        <a style="padding: 0; margin:0; font-size: 12px; font-weight: 500">2020109999</a>
      </div>
      <div class="wrap-menu">
        <ul>
          <li @click="toNotice" v-bind:class="{'selected-menu':menu.isNotice}" class="m-el notice">
            <img src="icon-notice.png" />
            <h4 class="menu-kor">공지사항</h4>
          </li>
          <li class="m-el">
            <img src="icon-planning.png" />
            <h4 class="menu-kor">종합시간표 조회</h4>
          </li>
          <li @click="toWishList" v-bind:class="{'selected-menu':menu.isWishList}" class="m-el">
            <img src="icon-subject.png"/>
            <h4 class="menu-kor">희망과목내역</h4>
          </li>
          <li @click="toCourseList" v-bind:class="{'selected-menu':menu.isCourseList}" class="m-el">
            <img src="icon-search.png" />
            <h4 class="menu-kor">수강신청내역</h4>
          </li>
          <li @click="toRegister" class="m-el registration" v-bind:class="{'selected-menu':menu.isRegister}">
            <img src="icon-registration.png" />
            <h4 class="menu-kor">수강신청</h4>
          </li>
        </ul>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data(){
    return {
      menu :{
      isCourseList:false,
      isRegister:false,
      isNotice:true,
      isWishList:false,
      }
    }
  },
  methods: {
    // 공지사항탭
    toNotice(){
       for(let menu in this.menu){
        menu === 'isNotice' ? this.menu[menu] = true : this.menu[menu] =false;
      }
      this.$emit('noticeMenu')
    }, 
    //희망과목탭
    toWishList(){
       for(let menu in this.menu){
        menu === 'isWishList' ? this.menu[menu] = true : this.menu[menu] =false;
      }
      this.$emit('wishMenu')
    },
    //신청내역탭
    toCourseList(){
      for(let menu in this.menu){
        menu === 'isCourseList' ? this.menu[menu] = true : this.menu[menu] =false;
      }
      this.$emit('courseMenu')
    },
    //수강신청탭
    toRegister(){
      for(let menu in this.menu){
        menu === 'isRegister' ? this.menu[menu] = true : this.menu[menu] =false;
      }
      this.$emit('registerMenu')
    }
  }

};
</script>

<style>
.re-sidebar{
    position: absolute;
    left: 0;
    top: 0;
    overflow-y: hidden;
    background-color: #253A73;
    width : 120px;
    height: 100%;
}
.wrapper .re-sidebar .re-nav{
    
    text-align: center;
} 
.re-nav h4{
   color : white ;
}
.re-myinfo{
  color : white ;
    background-color:#717075;
    padding-top: 7px;
    display: flex;
    flex-direction: column;
    height: 60px;
}
.name-kor{
    height:40px;
}
.m-el{ 
    height: 97px;
}
.m-el img{
    margin-top:25px;
    padding-bottom: 4px;
} 
.menu-kor{
    font-size: 12px;
    font-weight: 400;
}
.selected-menu{
    background-color: #B6985A;
}
</style>