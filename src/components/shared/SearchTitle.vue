<template>
  <div class="sw-header search-header">
    <h2>개설강좌 목록</h2>
    <div class="buttonset">
      <span class="item">총 조회건수<em class="totalSearchNumber">{{ searchNum }}</em>건</span
      >
    </div>
  </div>
</template>

<script>
export default {
  props:['searchNum']
};
</script>

<style>
</style>