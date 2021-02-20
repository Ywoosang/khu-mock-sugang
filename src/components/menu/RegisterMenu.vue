<template>
  <div class="content-wrapper">
    <modal
      @close="modalClose"
      @accept="modalAccept"
      v-if="isModal"
      v-bind:modalMessage="modalMessage"
      v-bind:courseDelete="isDelete"
    ></modal>
    <select-tab @tab="changeTab"></select-tab>

    <template v-if="defaultTab">
      <default-title @refresh="contentRefresh"></default-title>
      <default-content
        @apply="registerCourse"
        @save="contentSave"
        @refresh="contentRefresh"
        v-bind:refresh="refresh"
        v-bind:savedCourses="savedCourses"
        v-bind:courseFull="courseFull"
      ></default-content>
    </template>
    <template v-else>
      <search-title v-bind:searchNum="searchNum"></search-title>
      <search-content
        @apply="registerCourse"
        @searchNum="searchNumber"
        v-bind:modalPause="isModal"
      ></search-content>
    </template>
    <course-list
      @delete="deleteCourse"
      v-bind:courseList="courseList"
    ></course-list>
  </div>
</template>

<script>
import SelectTab from "../shared/SelectTab.vue";
import DefaultTitle from "../shared/DefaultTitle.vue";
import DefaultContent from "../shared/DefaultContent.vue";
import SearchTitle from "../shared/SearchTitle.vue";
import SearchContent from "../shared/SearchContent.vue";
import CourseList from "../shared/CourseList.vue";
import Modal from "../common/Modal.vue";

export default {
   props : ['Courses'],
  data() {
    return {
      // 모달 관련
      isModal: false,
      isDelete: false,
      modalMessage: null,
      // 상단 탭 선택
      defaultTab: true,
      // 수강신청 목록
      courseList: [],
      savedCourses: null,
      // 검색중일때
      pause: false,
      // 강좌 검색
      searchNum: 10,
      refresh : false,
    };
  },
  created() {
    window.addEventListener("keydown", (e) => {
      if (e.key.toLowerCase() === "escape") this.modalClose();
    });
    if(this.Courses!== []){
      // 변수명 추후에 변경
      this.courseList = this.Courses;
    }
  },
  computed: {
    courseFull() {
      if (this.courseList.length >= 7) return true;
      return false;
    },
  },
  components: {
    "default-title": DefaultTitle,
    "default-content": DefaultContent,
    SearchTitle,
    SearchContent,
    SelectTab,
    CourseList,
    modal: Modal,
  },
  methods: {
    contentRefresh(status){
      if(status=='start'){
        this.courseList = []; 
        this.refresh=true;
        this.$emit('reset')
      }else if(status=='end'){
        this.refresh=false;
      }
       
    },
    changeTab(num) {
      num == 0 ? (this.defaultTab = true) : (this.defaultTab = false);
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
      this.$emit('renewal',this.courseList);
    },
    modalClose() {
      if (this.timeOver) this.$emit("home");
      this.isModal = false;
      this.pause = false;
    },
    // 삭제확인일 경우
    modalAccept() {
      if (this.timeOver) this.$emit("home");
      if (this.isDelete) {
        this.isDelete = false;
        this.isModal = false;
        setTimeout(() => {
          this.isModal = true;
          this.showModal("삭제되었습니다.");
          this.courseList.pop();
          this.$emit('renewal',this.courseList);
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
</style>