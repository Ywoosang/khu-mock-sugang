<template>
  <div class="content-wrapper">
    <div class="notice-wrapper">
      <div class="time-notice">
        <div class="time-text">
          <p>
            <i
              style="color: rgb(235, 34, 34)"
              class="fas fa-exclamation-triangle"
            ></i>
            수강신청 로그인 가능시간이 아닙니다.
          </p>
          <p class="time-limit">가능시간까지 {{ timeLimit }}초 남았습니다.</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["timeLimit"],
};
</script>

<style>
.notice-wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
}
.time-notice {
  margin: 0 25px;
  width: inherit;
  height: 100px;
  background-color: #f2f5fc;
  border: 1px solid #b4b4b44b;
}
.time-notice .time-text {
  margin: 28px 15px 0 15px;
  font-weight: 400;
}
.time-notice .time-text .time-limit {
  margin-left: 18px;
}
</style>