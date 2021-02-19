<template>
  <div class="content-wrapper">
    <wish-title></wish-title>
    <div class="wish-content">
      <div class="itb-wrapper" style="overflow: hidden">
        <div class="itb wish-itms" style="overflow: hidden">
          <div class="itm">
            <a class="emt"></a>
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
            <a class="itm-lang">언어구분</a>
            <a class="itm-special">비고</a>
            <a style="width: 45px"></a>
          </div>
          <div
            class="itm"
            v-for="content of contents"
            v-bind:class="{
              'spare-itm': content.num >= 8,
            }"
            :key="content.num"
          >
            <a class="itm-num">{{ content.num }}</a>
            <a class="itm-clf">{{ content.division }}</a>
            <a class="itm-snum">ADD123-01</a>
            <a class="itm-cname">강좌 {{ content.num }}</a>
            <a class="itm-grd">0</a>
            <a class="itm-znum">30</a>
            <a class="itm-zanum">10</a>
            <a class="itm-stime"></a>
            <a class="itm-gname">교수{{ content.num }}</a>
            <a class="itm-hakzum">3</a>
            <a class="itm-time">월 10:30-13:00 (강의실)</a>
            <a class="itm-isgub">04</a>
            <a class="itm-lang">영어(부분)</a>
            <a class="itm-special"></a>
            <a style="width: 45px"></a>
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
          >이수구분 : 11 전공기초, 04 전공필수, 05 전공선택, 06 교직과, 14
          중핵교과, 15 배분이수교과, 16 기초교과, 17 자유이수, 20 교직전선, 24
          계절학기전공필수, 27 계절학기전공기초, 08
          자유선택교과[배움학점제,군사학,취업스쿨,학점교류 과목등]</a
        >
      </div>
    </div>
  </div>
</template>

<script>
import WishTitle from "../shared/DefaultTitle.vue";
export default {
  data() {
    return {
      contents: [],
    };
  },
  components: {
    "wish-title": WishTitle,
  },
  created() {
    const arr = Array.apply(null, { length: 10 }).map((_, index) => index + 1);
    arr.forEach((num) => {
      const obj = {};
      obj.num = num;
      num < 8 ? (obj.division = "희망과목") : (obj.division = "예비과목");
      this.contents.push(obj);
    });
  },
};
</script>

<style>
</style>