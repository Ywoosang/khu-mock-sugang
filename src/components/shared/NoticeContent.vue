<template>
  <div class="tab-select" @click="$emit('hideModal')">
    <button class="tab wish-selected">
      <img class="waf" src="bg-tab-left.png" alt="" />학부 수강신청공지
    </button>
    <button class="tab not-selected">학부 수강신청일정</button>
    <button class="tab not-selected">학부 계절학기 공지</button>
    <button class="tab not-selected">학부 계절학기 등록일정</button>
    <button class="tab not-selected">학부 희망과목 공지</button>
    <button class="tab not-selected">대학원 수강신청 공지</button>
    <button class="tab not-selected">신규 시스템 유의사항</button>
  </div>
</template>
<script>
export default {};
</script>

<style>
</style>