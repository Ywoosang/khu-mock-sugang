<template>
  <div class="wrapper">
    <modal-window
      @close="modalClose"
      @accept="modalAccept"
      v-if="isModal"
      v-bind:modalMessage="modalMessage"
    ></modal-window>
    <side-bar></side-bar>
    <section class="main">
      <app-header></app-header>
      <div class="content">
        <select-tab
          v-bind:defaultTab="defaultValue"
          @tab="changeTab"
        ></select-tab>
        <template v-if="defaultValue">
          <wish-title></wish-title>
          <wish-content
            @apply="registerCourse"
            v-bind:modalPause="isModal"
          ></wish-content>
        </template>

        <template v-else>
          <search-title></search-title>
          <search-content
            @apply="registerCourse"
            v-bind:modalPause="isModal"
            v-bind:isSearch="isSearch"
          ></search-content>
        </template>
      </div>
      <course-list @delete="deleteCourse" v-bind:courseList="courseList"></course-list>
    </section>
    <app-footer></app-footer>
  </div>
</template>

<script>
import AppHeader from "./components/AppHeader.vue";
import SideBar from "./components/SideBar.vue";
import SelectTab from "./components/SelectTab.vue";
import SearchTitle from "./components/SearchTitle.vue";
import WishTitle from "./components/WishTitle.vue";
import SearchContent from "./components/SearchContent.vue";
import WishContent from "./components/WishContent.vue";
import CourseList from "./components/CourseList.vue";
import AppFooter from "./components/AppFooter.vue";
import Modal from "./components/ModalWindow.vue";

export default {
  data() {
    return {
      defaultValue: true,
      isSearch: false,
      isModal: false,
      isDelete:false,
      modalMessage: null,
      courseList: [],
      pause:false,
    };
  },
  methods: {
    changeTab() {
      this.defaultValue = !this.defaultValue;
    },
    searchCourse(isSearch) {
      this.isSearch = isSearch;
    },
    deleteCourse(){
      this.isDelete = true; 
      setTimeout(()=>{
        this.courseList.pop();
        
      },1500)
    },
    showModal(msg) {
      this.isModal = true;
      this.modalMessage = msg;
    },
    registerCourse(num) {
      if(this.pause) return;
      this.pause =true;
      if (num === 10) {
        setTimeout(() => {
          this.showModal("수강 인원이 초과되었습니다.");
        }, 1500);
        return;
      }
      if (this.courseList.length === 7) {
        setTimeout(() => {
          this.showModal("이수가능학점을 초과했습니다.");
          this.courseList.push(this.courseList.length + 1);
        }, 1500);
        return;
      }
      setTimeout(() => {
        this.showModal("신청되었습니다.");
        this.courseList.push(this.courseList.length + 1);
      }, 1500);
    },
    modalClose() {
      this.isModal = false;
      this.pause =false; 
    },
    // 삭제확인일 경우
    modalAccept(isDelete){
      if (isDelete) {
        console.log("hi");
      }
      this.isModal = false;
      this.pause =false; 
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
  margin: 85px 25px 105px 25px;
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