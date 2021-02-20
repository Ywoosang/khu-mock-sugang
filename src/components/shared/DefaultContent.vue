<template>
  <div class="wish-content">
    <div class="itb-wrapper">
      <div class="itb wish-itms">
        <div class="itm">
          <a class="emt"></a>
          <a class="itm-apply">수강신청</a>
          <a class="itm-clf">구분</a>
          <a class="itm-snum">학수번호-분반</a>
          <a class="itm-cname">강좌명</a>
          <a class="itm-grd">대상학년</a>
          <a class="itm-znum">정원</a>
          <a class="itm-zanum">잔여인원</a>
          <a class="itm-stime">신청가능시간</a>
          <a class="itm-gname">교수명</a>
          <a class="itm-hakzum">학점</a>
          <a class="itm-time">강의시간/강의실</a>
          <a class="itm-isgub">이수구분</a>
          <a style="flex:1;"></a>
        </div>
        <div
          class="itm"
          v-for="content in contents"
          v-bind:class="{
            'spare-itm': content.num >= 8 && !content.registered,
            'selected-itm': content.registered,
          }"
          v-bind:key="content.num"
        >
          <a class="itm-num">{{ content.num }}</a>
          <a class="itm-apply">
            <button
              v-if="!content.registered"
              @click="() => courseApply(content.num)"
              class="apply-btn"
            >
              신청
            </button>
            <span v-else style="color: red">완료</span>
          </a>
          <a class="itm-clf">{{ content.division }}</a>
          <a class="itm-snum">ADD123-01</a>
          <a style="text-align:left;" class="itm-cname">{{ content.name }}</a>
          <a class="itm-grd">0</a>
          <a class="itm-znum">30</a>
          <a class="itm-zanum">10</a>
          <a class="itm-stime"></a>
          <a class="itm-gname">교수{{ content.num }}</a>
          <a class="itm-hakzum">3</a>
          <a class="itm-time">월 10:30-13:00 (강의실)</a>
          <a class="itm-isgub">04</a>
          <a style="flex:1;"></a>
        </div>
      </div>
    </div>
    <div class="itm-notice">
      <a
        ><i
          style="margin: 0 5px 0 15px; color: #39abd4; font-size: 20px"
          class="fas fa-exclamation-circle"
        >
        </i
        >희망과목 정원 및 잔여인원은 조회하는 시점 기준 인원으로 실시간
        변동되므로, <em>'새로고침'</em> 또는 <em>'수강신청'</em> 재클릭시 조회
        인원은 달라질 수 있습니다.</a
      >
    </div>
  </div>
</template>

<script>
export default {
  props: ["isSearch", "courseFull", "savedCourses","refresh"],
  data() {
    return {
      loading: true,
      contents: [],
      courseNum: "",
      rigisterPause: false,
    };
  },
  created() {
    setTimeout(() => {
      if (this.savedCourses !== null) {
        this.contents = this.savedCourses;
        return;
      }
      this.makeContents();
    }, 1500);
  },
  methods: {
    range: (l) => Array.apply(null, { length: l }).map((_, index) => index + 1),
    makeContents() {
      const arr = this.range(10);
      this.contents = arr.map((num) => {
        const obj = {};
        obj.num = num;
        obj.division = num <= 7 ? "희망과목" : "예비과목";
        obj.name = num !== 10 ? "신청연습" : "인원 초과 연습";
        obj.registered = false;
        return obj;
      });
    },
    courseApply(num) {
      if (this.rigisterPause) return;
      this.rigisterPause = true;
      new Promise((resolve) => {
        setTimeout(() => {
          this.$emit("apply", num);
          // 수강신청 내역이 다 찼거나 인원초과 연습 
          if (this.courseFull || num === 10) {
            this.rigisterPause = false;
            return;
          }
          resolve();
        }, 1500);
      }).then(() => {
        this.doneContents(num);
        this.$emit("save", this.contents);
        this.rigisterPause = false;
      });
    },
    doneContents(num) {
      this.contents.filter((el, index) => {
        if (index + 1 === num) {
          el.registered = true;
        }
        return el;
      });
    },
        
  },
   watch: {
      refresh(){
        this.$emit('refresh','end') 
        this.contents=[];
        setTimeout(() => {
          this.makeContents();
      }, 500);
      }
   }
  };
</script>

<style>
 
 
</style>