<template>
  <div class="content susin-list">
    <div class="itb-title">
      <a style="letter-spacing: -2px;color:#333333; font-weight: 600; font-size: 16px"
        >수강신청내역</a
      >
      <a class="buttonset">
        <span class="item" id="meta_3">총 신청가능학점<em> 21</em>학점</span>
        <span class="item" id="meta_4"
          >신청과목수<em class="totalNumber">{{ courseList.length }}</em>과목</span
        >
        <span class="item" id="meta_5"
          >신청학점<em class="totalScore">{{ courseList.length*3 }}</em>학점</span
        >
      </a>
    </div>
    <!-- item block wrapper -->
    <div class="itb-cover">
      <div style="width: 100%" class="itb susin">
        <div class="itm susin-itm">
          <a class="itm-num"></a>
          <a v-if="!listMenu" class="itm-apply" style="width: 70px">수강삭제</a>
          <a class="itm-snum">학수번호-분반</a>
          <a class="itm-cname">강좌명</a>
          <a class="itm-grd">대상학년</a>
          <a class="itm-gname">교수명</a>
          <a class="itm-hakzum">학점</a>
          <a class="itm-time">강의시간/강의실</a>
          <a class="itm-isgub">이수구분</a>
          <a class="itm-zsugang">재수강 여부</a>
          <a class="itm-bigo">비고</a>
          <a style="flex:4;"></a>
        </div>
        <div class="noCourses" v-if="noCourses">
          <a>수강신청 내역이 없습니다.</a>
        </div> 
        <div v-for="num in courseList" :key="num" class="itm susin-itm">
          <a class="itm-num">{{ num }}</a>
          <a v-if="!listMenu" class="itm-apply" style="width: 70px"
            ><button @click="()=>deleteCourse(num)" class="delete-btn">삭제</button></a
          >
          <a class="itm-snum">ADD123-01</a>
          <a style="text-align:left;" class="itm-cname">삭제연습{{ num }}</a>
          <a class="itm-grd">0</a>
          <a class="itm-gname">교수{{ num }}</a>
          <a class="itm-hakzum">3</a>
          <a class="itm-time">월 10:30-13:00 (강의실)</a>
          <a class="itm-isgub">이수구분</a>
          <a class="itm-zsugang"></a>
          <a class="itm-bigo"></a>
          <a style="flex:4;"></a>
        </div>
      </div>
    </div>
    <!--  -->
    <div class="itm-warn itm-notice">
      <a
        ><i class="fas fa-exclamation-circle"> </i> 이수구분 : 11 전공기초, 04
        전공필수, 05 전공선택, 06 교직과, 14 중핵교과, 15 배분이수교과, 16
        기초교과, 17 자유이수, 20 교직전선, 24 계절학기전공필수, 27
        계절학기전공선택, 08 자유선택교과[배움학점제,군사학,취업스쿨,학점교류
        과목등]</a
      >
    </div>
  </div>
</template>

<script>
export default {
  props: ["courseList","listMenu"],
  methods :{
      deleteCourse(num){
          this.$emit('delete',num)
      }
  },
  computed : {
    noCourses(){
      return this.courseList.length===0 ? true : false;
    }
  }

};
</script>

<style>
.itb-title {
    color: black;
    font-weight: 500;
    margin: 15px 0 0 0;
    height: 42px;
    line-height: 42px;
  }
  .susin-itm {
    display: flex;
    justify-content: flex-start;
  }
  .itm .itm-time {
    text-align: center;
  }
  .susin-list {
    position: relative;
    border: none;
    height: 550px;
    margin-bottom: 60px;
  }
  .susin {
    width: inherit;
  }
  .susin-title,
  .susin-itm {
    width: inherit;
    overflow: hidden;
  }
  .itb-cover {
    min-width: 1160px;
    border: 1px solid #d5d9e0;
    width: inherit;
    display: flex;
    flex-direction: column;
    height: 450px;
  }
  .delete-btn {
    cursor: pointer;
    display: inline-block;
    width: 56px;
    height: 28px;
    border-radius: 3px;
    padding: 0px 8px 2px;
    background-color: #d55e5f;
    color: white;
    border: 1px solid rgb(184, 17, 17);
  }
  .delete-btn:hover {
    background-color: rgba(175, 10, 10, 0.842);
  }
  .buttonset {
    float: right;
  }
  .item {
    margin: 0 15px;
    font-weight: 400;
    font-size: 14px;
    position: relative;
  }
  .item:nth-child(1)::after,
  .item:nth-child(2)::after {
    content: "";
    width: 1px;
    height: 12px;
    top: 5px;
    right: -17px;
    position: absolute;
    background-color: #ddd;
  }
  .item em {
    font-style: normal;
    font-weight: 700;
    font-size: inherit;
    color: #fe842f;
  }
  .susin-warn {
    width: 1660px;
    position: absolute;
    bottom: -39px;
    left: 0;
  }
  .noCourses{
    width : inherit;
    height: 440px;
    position:relative;
    text-align: center;
  }
  .noCourses a{
    position:absolute;
    top: 50px;
    font-size: 15px;
    font-weight: 400;
  }
</style>