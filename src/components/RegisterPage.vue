<template>
  <div class="wrapper">
    <modal-window
      @close="modalClose"
      @accept="modalAccept"
      v-if="isModal"
      v-bind:modalMessage="modalMessage"
      v-bind:courseDelete="isDelete"
    ></modal-window>
    <side-bar
    @noticeMenu="toNoticeMenu"
    @courseMenu="toCourseMenu"
    @registerMenu="toRegisterMenu"
    ></side-bar>
    <section class="main">
      <app-header ></app-header>
      <notice-menu v-if="noticeMenu"></notice-menu>
      <div v-if="contentTotal" class="content">
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
          <search-title></search-title>
          <search-content
            @apply="registerCourse"
            v-bind:modalPause="isModal"
            v-bind:isSearch="isSearch"
          ></search-content>
        </template>
      </div>
      <course-list v-if="listTotal" @delete="deleteCourse" v-bind:courseList="courseList"></course-list>
    </section>
    <app-footer></app-footer>
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
import NoticeMenu from "./NoticeSection.vue";

export default {
  data() {
    return {
      defaultValue: true,
      isSearch: false,
      isDelete:false,
      isModal:false,
      modalMessage: null,
      courseList: [],
      savedCourses:null,
      pause:false,
      //탭 변경
      contentTotal:false,
      listTotal:false, 
      noticeMenu:true,
      // 수강신청 내역일 경우
    };
  },
  computed:{
    courseFull(){
      // if(this.courseList.length >= 7) return true;
      return false; 
    } 
  },
  methods: {
    // 메뉴 변경
    toNoticeMenu(){
        this.noticeMenu=true;
        this.listTotal=false;
        this.contentTotal=false;
    },
    toCourseMenu(){
        this.noticeMenu=false;
        this.contentTotal = false;
        this.listTotal = true; 
    },
    toRegisterMenu(){
        this.noticeMenu=false;
        this.contentTotal = true;
        this.listTotal = true; 
    },
    // 수강신청 페이지
    changeTab() {
      this.defaultValue = !this.defaultValue;
    },
    searchCourse(isSearch) {
      this.isSearch = isSearch;
    },
    deleteCourse(num){
        // 삭제문구 전송
      if(this.pause) return;
      this.pause =true;
      this.isDelete = true;
      this.showModal(`[삭제연습${num}] 을 삭제 하시겠습니까?`)
    },
    showModal(msg) {
    // 모달창 생성 
      this.isModal = true;
      this.modalMessage = msg;
    },
    registerCourse(num) {
      this.isDelete =false; 
      if(this.pause) return;
      this.pause =true;
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
      this.isModal = false;
      this.pause =false; 
    },
    // 삭제확인일 경우
    modalAccept(){
      if(this.isDelete) {
        this.isDelete=false;
        this.isModal = false;
        setTimeout(()=>{
            this.isModal=true; 
            this.showModal('삭제되었습니다.');
            this.courseList.pop();
        },1700);
      }
      this.isModal = false;
      this.pause =false; 
    },
    contentSave(contents){
      this.savedCourses = contents; 
    }
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
    "notice-menu": NoticeMenu,
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Noto+Sans+KR:wght@100;300;400;500&display=swap");
html,
body {
  height: 100%;
  width: 100%;
  margin: 0;
  font-family: "Noto Sans KR", sans-serif;
  font-weight: 300;
}
body {
  position: relative;
}
div {
  box-sizing: border-box;
}
ul,
li {
  list-style: none;
  margin: 0;
  padding: 0;
}
section,
article {
  margin: 0;
}
h1,
h2,
h3,
h4,
h5,
h6 {
  margin: 0;
}
button {
  outline: none;
  border: none;
}

.wrapper {
  width: calc(100vw - 125px);
  height: inherit;
  position: relative;
}
.main {
  position: absolute;
  top: 0;
  height: inherit;
  width: inherit;
  margin-left: 120px;
  position: relative;
  overflow: auto;
}

.content {
  width: 1660px;
  margin: 75px 25px 105px 25px;
  font-size: 0;
}
/* 공통 클래스 추가 */

.hide {
  display: none;
}
.red {
  color: red;
}
.itm:hover {
  background-color: rgb(250, 250, 250);
}

/* 공통 미디어쿼리 */
@media screen and (min-width: 1820px) {
  footer {
    bottom: 0;
  }
}
@media (min-width: 320px) and (max-width: 480px) {
  footer {
    display: none;
  }
}
</style>