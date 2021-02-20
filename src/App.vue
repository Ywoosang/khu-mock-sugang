<template>
  <div class="main">
    <modal
      v-if="isModal"
      v-bind:modalMessage="modalMessage"
      @accept="renderHome"
      @close="renderHome"
    ></modal>
    <template v-if="home">
      <home-header @home="renderHome"></home-header>
      <home-page @register="startTest" @home="renderHome"></home-page>
    </template>
    <template v-else>
      <course-header @home="renderHome" @timeOver="changeTimeOver"></course-header>
      <course-page
        @home="renderHome"
        v-bind:timeLimit="timeLimit"
        v-bind:menu="menu"
      ></course-page>
    </template>
    <side-bar v-bind:homePage="home" @changeMenu="changeMenu"></side-bar>
  </div>
</template>
 
<script>
import CoursePage from "./components/CoursePage.vue";
import HomePage from "./components/HomePage.vue";
import SideBar from "./components/common/SideBar.vue";
import Modal from "./components/common/Modal.vue";
import HomeHeader from "./components/common/HomeHeader.vue";
import CourseHeader from "./components/common/CourseHeader.vue";
export default {
  data() {
    return {
      // 헤더에서 시간종료
      //수강신청 시작시 기다리는 시간
      timeLimit: 20,
      // 홈페이지 여부
      home: true,
      // 기본적으로 공지사항 탭으로 이동
      menu: "noticeMenu",
      // 시간 초과 모달
      isModal: false,
      modalMessage: "장시간 사용이 없어서 자동로그아웃 됩니다!",
    };
  },
  methods: {
    // 체인지 이벤트 받은 후 인자를 데이터에 바인딩해서 전달
    changeMenu(menu) {
      if (this.home == true) return;
      this.menu = menu;
    },
    renderHome() {
      this.isModal = false;
      this.timeOver = false;
      this.timeLimit = 0;
      this.home = true;
      location.reload();
    },
    startTest() {
      const timmer = setInterval(() => {
        this.timeLimit--;
      }, 1000);
      if (this.timeLimit == 0) {
        clearInterval(timmer);
        // 사전 오류 방지
        this.timeLimit = 0;
      }
      this.home = false;
    },
    changeTimeOver() {
      this.isModal = true;
    },
  },
  components: {
    "course-page": CoursePage,
    "home-page": HomePage,
    SideBar,
    Modal,
    HomeHeader,
    CourseHeader,
  },
};
</script>

<style>
</style>