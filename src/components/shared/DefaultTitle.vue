<template>
  <div class="sw-header wish-header">
    <h2>수강희망과목</h2>
    <div class="buttonset">
      <span class="item">총 조회건수<em>10</em>건</span>
      <button @click="$emit('refresh','start')" type="button" class="btn-icon">
        <i class="fas fa-redo-alt"></i>
        <span>새로고침</span>
      </button>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style>
.sw-header {
    overflow: hidden;
    height: 42px;
    margin-top: 15px;
    display: flex;
    justify-content: space-between;
  }
  .sw-header h2 {
    float: left;
    margin-top: 6px;
    font-size: 16px;
    font-weight: 700;
    letter-spacing: -2px;
    word-spacing: -1px;
  }
  .sw-header .item {
    position: relative;
    top: 4px;
    margin-left: 1px;
    padding: 0 15px;
    font-size: 14px;
  }
  .sw-header button {
    position: relative;
    margin: 0 3px;
    border-radius: 3px;
    border: 1px solid;
    font-weight: 400;
    letter-spacing: 0;
    text-align: center;
    cursor: pointer;
    overflow: hidden;
    box-sizing: border-box;
    height: 34px;
    padding: 0 12px;
    font-size: 13px;
    background-color: #fff;
    border-color: #666;
    color: #333;
  }
  .sw-header .btn-icon:hover {
    background-color: #f7f7f7;
    border-color: #666;
    color: #333;
}

</style>