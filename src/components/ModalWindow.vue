<template>
  <div class="modal-window">
    <div class="modal">
      <div class="top">
        <a class="modal-notice"
          ><span style="font-weight: 400; font-size: 18px">알림</span
          >(notice)</a
        >
        <button class="modal-close"></button>
      </div>
      <div class="middle">
        <a
          ><span style="color: rgb(226, 0, 0)"
            ><i class="fas fa-exclamation-triangle"></i></span
          ><span style="font-size: 13px"> ${ text }</span></a
        >
      </div>
      <div class="bottom">
        <button class="gomain-btn">확인</button>
      </div>
    </div>
    <div class="modal">
      <div class="top">
        <a class="modal-notice"
          ><span style="font-weight: 400; font-size: 18px">알림</span
          >(notice)</a
        >
        <button class="modal-close"></button>
      </div>
      <div class="middle">
        <a
          ><span style="color: rgb(226, 0, 0)"
            ><i class="fas fa-exclamation-triangle"></i></span
          ><span style="font-size: 13px"
            >[삭제연습]을 삭제 하시겠습니까?</span
          ></a
        >
      </div>
      <div class="bottom">
        <button class="gomain-btn">확인</button
        ><button class="cancel-btn">취소</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style>
.modal-window {
  position: absolute;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  z-index: 1001;
  background-color: rgba(0, 0, 0, 0.7);
}
.modal {
  z-index: 1001;
  color: black;
  position: absolute;
  left: 50%;
  top: 40%;
  transform: translate(-50%);
  width: 320px;
  height: 162px;
  background-color: white;
  opacity: 1;
  border: 1px solid #ddd;
}
.modal .top {
  height: 50px;
  background-color: #f8fcf2;
  line-height: 45px;
  padding-left: 10px;
  position: relative;
  border-bottom: 1px solid #ddd;
}
.modal .top::after {
  content: "";
  background-color: rgb(105, 105, 105);
  width: 1px;
  height: 20px;
  position: absolute;
  top: 14px;
  right: 20px;
  transform: rotate(45deg);
}
.modal .top::before {
  content: "";
  background-color: rgb(105, 105, 105);
  width: 1px;
  height: 20px;
  position: absolute;
  top: 14px;
  right: 20px;
  transform: rotate(-45deg);
  pointer-events: none;
}
.modal .modal-close {
  position: absolute;
  height: 35px;
  width: 35px;
  padding: 0;
  top: 5px;
  right: 5px;
  background-color: transparent;
}
.modal .middle {
  text-align: center;
  height: 58px;
  line-height: 50px;
  border-bottom: 1px solid #ddd;
}
.modal .bottom {
  height: 54px;
  text-align: center;
  line-height: 40px;
}
.modal .bottom .gomain-btn {
  width: 56px;
  height: 28px;
  background-color: #253a73;
  color: white;
  border-radius: 2px;
}
.modal .bottom .gomain-btn:hover {
  background-color: #1e2f5d;
}
/* 취소버튼 있는 삭제모달 */
.cancel-btn {
  width: 60px;
  height: 34px;
  border: 1px solid gray;
  border-radius: 3px;
  background-color: white;
}
</style>