<template>
  <div class="nav">
    <div
      v-if="homePage"
      :style="{ background: '#747378 url(icon-login.png) no-repeat 50% 21px' }"
      class="login"
      style="cursor:not-allowed;"
    >
      로그인
    </div>

    <div v-else>
      <div class="myinfo"  style="cursor:grab;">
        <span class="name-kor">KYUNG HEE</span>
        <span class="name-eng">2020109999</span>
      </div>
    </div>
    <div class="wrap-menu">
      <ul>
        <li
          @click="toNotice" 
          v-bind:class="{ 'selected-menu': menu.isNotice && !homePage }"
          class="notice"
        >
          <img src="icon-notice.png" />
          <span class="menu-kor">공지사항</span>
        </li>
        <li style="cursor:not-allowed;"
        >
          <img src="icon-planning.png" />
          <span class="menu-kor">종합시간표 조회</span>
        </li>
        <li
          @click="toWishList"
          v-bind:class="{ 'selected-menu': menu.isWishList }"
        >
          <img src="icon-subject.png" />
          <span class="menu-kor">희망과목내역</span>
        </li>
        <li
          @click="toCourseList"
          v-bind:class="{ 'selected-menu': menu.isCourseList }"
        >
          <img src="icon-search.png" />
          <span class="menu-kor">수강신청내역</span>
        </li>
        <li
          @click="toRegister"
          class="m-el registration"
          v-bind:class="{ 'selected-menu': menu.isRegister }"
        >
          <img src="icon-registration.png" />
          <span class="menu-kor">수강신청</span>
        </li>
      </ul>
    </div>
  </div>
</template> 

<script>
export default {
  props: ["homePage"],
  data() {
    return {
      menu: {
        isCourseList: false,
        isRegister: false,
        isNotice: true,
        isWishList: false,
      },
    };
  },
  methods: {
    // 공지사항탭
    toNotice() {
       if (this.homePage) {
        alert("로그인이 필요한 서비스입니다.\n 로그인 화면으로 이동합니다.");
        location.reload();
        return;
      }
      // 로그인하지 않은 상황
      for (let menu in this.menu) {
        menu === "isNotice"
          ? (this.menu[menu] = true)
          : (this.menu[menu] = false);
      }
      this.$emit("changeMenu", "noticeMenu");
    },
    //희망과목탭
    toWishList() {
      if (this.homePage) {
        alert("로그인이 필요한 서비스입니다.\n 로그인 화면으로 이동합니다.");
        location.reload();
        return;
      }
      for (let menu in this.menu) {
        menu === "isWishList"
          ? (this.menu[menu] = true)
          : (this.menu[menu] = false);
      }
      this.$emit("changeMenu", "wishMenu");
    },
    //신청내역탭
    toCourseList() {
      if (this.homePage) {
        alert("로그인이 필요한 서비스입니다.\n 로그인 화면으로 이동합니다.");
        location.reload();
        return;
      }
      for (let menu in this.menu) {
        menu === "isCourseList"
          ? (this.menu[menu] = true)
          : (this.menu[menu] = false);
      }
      this.$emit("changeMenu", "listMenu");
    },
    //수강신청탭
    toRegister() {
      if (this.homePage) {
        alert("로그인이 필요한 서비스입니다.\n 로그인 화면으로 이동합니다.");
        location.reload();
        return;
      }
      for (let menu in this.menu) {
        menu === "isRegister"
          ? (this.menu[menu] = true)
          : (this.menu[menu] = false);
      }
      this.$emit("changeMenu", "registerMenu");
    },
  },
};
</script>

<style>
.nav {
  position: fixed;
  top: 0;
  left: 0;
  bottom: 0;
  z-index: 5;
  width: 120px;
  background: #253a73;
  transition: all 0.4s;
}
.nav .myinfo {
    position: relative;
    width: 100%;
    height: 60px;
    padding-top: 9px;
    background: #717075;
    text-align: center;
    box-sizing: border-box;
    cursor: pointer;
}
.nav .myinfo .name-kor {
    font-size: 16px;
    color: #fff;
}
.nav .myinfo .name-eng {
    position: relative;
    top: -2px;
    font-size: 12px;
    color: #fff;
}
.login {
  display: block;
}
.nav .login {
  position: relative;
  width: 100%;
  height: 94px;
  padding-top: 56px;
  /* background: #747378 url(./img/icon-login.png) no-repeat 50% 21px; */
  font-size: 16px;
  font-weight: bold;
  color: #fff;
  text-align: center;
  box-sizing: border-box;
}
.nav.login .wrap-menu {
  height: calc(100% - 184px);
}
.nav .wrap-menu > ul {
  position: absolute;
  width: 100%;
}
.nav .wrap-menu > ul > li {
  cursor: pointer;
  position: relative;
  width: 100%;
  padding: 20px 0;
  text-align: center;
}
.nav .wrap-menu > ul > li img {
  margin-bottom: 5px;
}
.nav .wrap-menu > ul > li [class^="menu"] {
  font-size: 12px;
  width: 100%;
  color: #fff;
  line-height: 1.4;
}
/* 푸터 */
.container .footer {
  width: 100%;
  height: 35px;
  line-height: 35px;
  background: #f0f0f0;
  font-size: 11px;
  color: #999;
  text-align: center;
}
.selected-menu {
  background-color: #b6985a;
}
</style>