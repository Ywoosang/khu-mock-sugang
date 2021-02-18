<template>
  <div class="main">
    <modal-window
      @close="modalClose"
      @accept="modalAccept"
      v-if="isModal"
      v-bind:modalMessage="modalMessage"
      v-bind:courseDelete="isDelete"
    ></modal-window>
    <app-header @home="goHomePage" @timeOver="goTimeOutHomePage"></app-header>

    <div class="container">
      <div class="content-wrapper">
        <notice-content @home="goHomePage" v-if="noticeMenu"></notice-content>
        <notice-modal @home="goHomePage" v-if="noticeMenu"> </notice-modal>
        <wish-menu v-if="wishMenu"></wish-menu>
        <time-limit
          v-if="timeLimit > 0 && registerMenu"
          v-bind:timeLimit="timeLimit"
        ></time-limit>
      </div>
      <div v-if="contentTotal && timeLimit <= 0" class="content-wrapper">
        <select-tab
          v-bind:defaultTab="defaultValue"
          @tab="changeTab"
        ></select-tab>
        <template v-if="defaultValue">
          <wish-title></wish-title>
          <wish-content
            @apply="registerCourse"
            @save="contentSave"
            v-bind:savedCourses="savedCourses"
            v-bind:courseFull="courseFull"
          ></wish-content>
        </template>
        <template v-if="!defaultValue">
          <search-title v-bind:searchNum="searchNum"></search-title>
          <search-content
            @apply="registerCourse"
            @searchNum="searchNumber"
            v-bind:modalPause="isModal"
            v-bind:isSearch="isSearch"
          ></search-content>
        </template>
        <course-list
          v-if="(timeLimit <= 0 || courseMenu) && listTotal"
          @delete="deleteCourse"
          v-bind:courseList="courseList"
          v-bind:courseMenu="courseMenu"
        ></course-list>
        <app-footer></app-footer>
      </div>
    </div>
    <side-bar></side-bar>
  </div>
</template>

<script>
import AppHeader from "./AppHeader.vue";
import SideBar from "./SideBar.vue";
import SelectTab from "./SelectTab.vue";
import SearchTitle from "./SearchTitle.vue";
import WishTitle from "./WishTitle.vue";
import SearchContent from "./SearchContent.vue";
import WishContent from "./WishContent.vue";
import CourseList from "./CourseList.vue";
import AppFooter from "./AppFooter.vue";
import Modal from "./ModalWindow.vue";
import NoticeModal from "./NoticeModal.vue";
import NoticeContent from "./NoticeContent.vue";

import WishMenu from "./WishSection.vue";
import TimeLimit from "./TimeLimit.vue";

export default {
  props: ["timeLimit"],
  data() {
    return {
      defaultValue: true,
      isSearch: false,
      isDelete: false,
      isModal: false,
      modalMessage: null,
      courseList: [],
      savedCourses: null,
      pause: false,
      //
      searchNum: 10,
      //탭 변경
      contentTotal: false,
      listTotal: false,
      noticeMenu: true,
      wishMenu: false,
      // 수강신청 내역일 경우
      courseMenu: false,
      registerMenu: false,
      // 시간초과시 메인으로
      timeOut: false,
      //
    };
  },
  created() {
    window.addEventListener("keydown", (e) => {
      if (e.key.toLowerCase() === "escape") this.modalClose();
    });
  },
  computed: {
    courseFull() {
      if (this.courseList.length >= 7) return true;
      return false;
    },
  },
  methods: {
    // 메뉴 변경
    toNoticeMenu() {
      this.registerMenu = false;
      this.wishMenu = false;
      this.noticeMenu = true;
      this.listTotal = false;
      this.contentTotal = false;
    },
    toWishMenu() {
      this.registerMenu = false;
      this.wishMenu = true;
      this.noticeMenu = false;
      this.listTotal = false;
      this.contentTotal = false;
      //
    },
    toCourseMenu() {
      this.registerMenu = false;
      this.wishMenu = false;
      this.noticeMenu = false;
      this.contentTotal = false;
      this.listTotal = true;
      //
      this.courseMenu = true;
    },
    toRegisterMenu() {
      this.registerMenu = true;
      this.wishMenu = false;
      this.noticeMenu = false;
      this.contentTotal = true;
      this.listTotal = true;
      //
      this.courseMenu = false;
    },
    // 수강신청 페이지
    changeTab() {
      this.defaultValue = !this.defaultValue;
    },
    searchCourse(isSearch) {
      this.isSearch = isSearch;
    },
    deleteCourse(num) {
      // 삭제문구 전송
      if (this.pause) return;
      this.pause = true;
      this.isDelete = true;
      this.showModal(`[삭제연습${num}] 을 삭제 하시겠습니까?`);
    },
    showModal(msg) {
      // 모달창 생성
      this.isModal = true;
      this.modalMessage = msg;
    },
    registerCourse(num) {
      this.isDelete = false;
      if (this.pause) return;
      this.pause = true;
      if (num === 10) {
        this.showModal("수강 인원이 초과되었습니다.");
        return;
      }
      if (this.courseList.length >= 7) {
        this.showModal("이수가능학점을 초과했습니다.");
        return;
      }
      this.showModal("신청되었습니다.");
      this.courseList.push(this.courseList.length + 1);
    },
    modalClose() {
      if (this.timeOut) this.$emit("timeOver");
      this.isModal = false;
      this.pause = false;
    },
    // 삭제확인일 경우
    modalAccept() {
      if (this.timeOut) this.$emit("timeOver");
      if (this.isDelete) {
        this.isDelete = false;
        this.isModal = false;
        setTimeout(() => {
          this.isModal = true;
          this.showModal("삭제되었습니다.");
          this.courseList.pop();
        }, 1700);
      }
      this.isModal = false;
      this.pause = false;
    },
    contentSave(contents) {
      this.savedCourses = contents;
    },
    searchNumber(num) {
      this.searchNum = num;
    },
    goTimeOutHomePage() {
      this.showModal("장시간 사용이 없어서 자동로그아웃 됩니다!");
      this.timeOut = true;
    },
    goHomePage() {
      this.$emit("home");
    },
  },
  components: {
    "app-header": AppHeader,
    "side-bar": SideBar,
    "select-tab": SelectTab,
    "search-title": SearchTitle,
    "wish-title": WishTitle,
    "search-content": SearchContent,
    "wish-content": WishContent,
    "course-list": CourseList,
    "app-footer": AppFooter,
    "modal-window": Modal,
    "wish-menu": WishMenu,
    "time-limit": TimeLimit,
    "notice-modal": NoticeModal,
    "notice-content": NoticeContent,
  },
};
</script>

<style>
.content-wrapper {
  padding: 15px 25px 25px;
  overflow: hidden;
  min-height: calc(100% - 35px);
  padding-bottom: 0;
}
.itm:hover {
  background-color: rgb(250, 250, 250);
}
</style>