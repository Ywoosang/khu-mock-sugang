<template>
  <div class="notice-modal">
        <div class="title">
           <div class="title-text">
            <span>0000학년도 0학기 수강신청</span>
            <a>로그아웃</a>
           </div>
        </div>
        <div class="main-text">
           <div>
               <span><b>성명</b></span>
               <span>테스트 유저</span>
           </div>
           <div>
            <span><b>학번</b></span>
            <span>1234567890</span>
           </div>
           <div>
            <span><b>학과</b></span>
            <span>소프트웨어 융합대학 소프트웨어 융합학과</span>
           </div>
           <div>
            <span><b>학년</b></span>
            <span>0학년</span>
           </div>
            <div>
            <span><b>수강가능학점</b></span>
            <span>
                <p>21</p>
                <p>학점</p>
            </span>
            </div>
        </div>
  </div>
</template>

<script>
export default {};
</script>

<style>
.notice-modal {
  z-index: 1001;
  width: 388px;
  height: 450px;
  position: absolute;
  top: 0;
  left: 16px;
  /* 스타일 삽입 */
}
.notice-modal::before {
  content: "";
  width: 16px;
  height: 16px;
  position: absolute;
  top: 25px;
  border-left: 1px solid lightgray;
  border-bottom: 1px solid lightgray;
  left: -9px;
  background-color: #f2f5fc;
  transform: rotate(45deg);
}
.notice-modal .title {
  border: 1px solid lightgray;
  border-bottom: none;
  width: inherit;
  height: 120px;
  background-color: #f2f5fc;
  box-sizing: border-box;
}
.notice-modal .title-text {
  display: flex;
}
.title-text span {
  margin-top: 42px;
  margin-left: 31px;
}
.title-text a {
  margin-top: 42px;
  margin-left: 43px;
  width: 88px;
  height: 45px;
  line-height: 45px;
  background-color: #253a73;
  border-radius: 4px;
  text-align: center;
  color: white;
  font-weight: bold;
  font-size: 15px;
}
.notice-modal .main-text {
  border: 1px solid lightgray;
  border-top: none;
  width: inherit;
  height: 329px;
  background-color: #ffffff;
}
.main-text div {
  border-bottom: 1px solid lightgray;
  width: 328px;
  height: 64px;
  margin-left: 32px;
}
.main-text div span {
  line-height: 64px;
}
.main-text div span:nth-child(1) {
  float: left;
  font-size: 14px;
}
.main-text div span:nth-child(2) {
  float: right;
  font-size: 15px;
}
.main-text div:last-child {
  border: none;
}
.main-text div span p:nth-child(1) {
  width: 26px;
  height: 26px;
  border-radius: 50%;
  background-color: #fe842f;
  position: absolute;
  margin-top: 18px;
  left: 295px;
  color: white;
  text-align: center;
  line-height: 26px;
  display: inline-block;
}
.main-text div span p:nth-child(2) {
  position: absolute;
  width: 40px;
  height: 40px;
  top: 365px;
  left: 328px;
}
</style>