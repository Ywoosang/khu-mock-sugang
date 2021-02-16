<template>
  <section class="sidebar">
    <div class="nav">
      <div class="myinfo">
        <a style="font-weight: 400">KYUNG HEE</a>
        <a style="padding: 0; font-size: 12px; font-weight: 500">1234567890</a>
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
          <li @click="toWishList" class="m-el">
            <img src="icon-subject.png" />
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
.sidebar{
    position: absolute;
    left: 0;
    top: 0;
    overflow-y: hidden;
    background-color: #253A73;
    width : 120px;
    height: 100%;
}
.nav{
    color : white;
    text-align: center;
} 
.myinfo{
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