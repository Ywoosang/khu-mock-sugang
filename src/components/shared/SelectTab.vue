<template>
  <div class="tab-select">
    <button @click="wishClick"  v-bind:class="[ wishTab ? 'wish-selected' : 'not-selected']" class="tab">
      <img  v-if="wishTab" class="waf" src="bg-tab-left.png" alt="" />수강희망과목
    </button>
    <button  @click="searchClick" v-bind:class="[ searchTab ? 'search-selected':'not-selected']" class="tab" >
        <!-- hide 로 가리기 -->
      <img v-if="searchTab" class="saf" src="bg-tab-right.png" alt="" />개설강좌검색
    </button>
  </div>
</template>

<script>
// 클릭시 자체적으로 변경하고, 이벤트로 부모요소에 보내주기
export default {
  data() {
    return {
      wishTab :true,
      searchTab : false,
    }
  },
  methods : {
    wishClick(){
      // 기존 값과 반대
      const newValue = !this.wishTab 
      // 선택되지 않은 상황이였다면
      if(newValue == true){
        this.$emit('tab',0) 
        this.wishTab = true;
        this.searchTab = false; 
      }
    },
    searchClick(){
      // 기존 값과 반대 
      const newValue = !this.searchTab 
       // 선택되지 않은 상황이였다면
       if(newValue == true){
        this.$emit('tab',1)
        this.searchTab = true; 
        this.wishTab = false;
      }
    }
  }
};
</script>

<style>
.tab-select {
    width:inherit;
    height: 43px;
    border-bottom: 1px solid #b6985a;
    padding: -1px;
  }
  .tab-select button img{
    pointer-events: none;
  }
  .tab-select .tab{
    cursor: pointer;
      height:42px;
      padding: 0 20px;
      margin:0;
  }
  /* 수강희망과목이 선택되었을때 */
  .tab-select .wish-selected,
  .tab-select  .search-selected {
    background-color: #b6985a;
    color: white;
    font-weight: bold;
    border: 1px solid #ad883f;
    border-right: none;
    border-bottom: none;
    border-radius: 6px 6px 0 0;
    position: relative;
  }
  .tab-select .wish-selected .waf {
    width: 18px;
    height: 43px;
    position: absolute;
    right: -18px;
    top: -1px;
  }
  .tab-select .search-selected .saf {
    width: 18px;
    height: 43px;
    position: absolute;
    right: -13px;
    top: -1px;
  }
  .tab-select  .not-selected {
    background-color: #e1e1e1;
    color: #777777;
    font-weight: bold;
    border: 1px solid rgb(199, 199, 199);
    border-bottom: none;
    border-radius: 6px 6px 0 0;
  }  

  /* 콘텐츠 영역 */
  .itb-wrapper {
    display: flex;
    border: 1px solid rgb(236, 236, 236);
    width: inherit;
    overflow: auto;
  }
  .itb-exp {
    height: 47px;
  }
  .itb {
     flex:1;
    padding-top: 1px;
    border-top: 1px solid rgba(61, 177, 255, 0.472);
    width: 1731px;
  }
  .itm {
    font-size: 12px;
    height: 45px;
    z-index: 5;
    border-bottom: 1px solid rgba(221, 221, 221);
    text-align: center;
    display:flex;
  }
  .itm:hover {
  background-color: rgb(250, 250, 250);
  }
  .itm:last-child {
    margin-bottom: 35px;
  }
  .itm a {
    float: left;
    height: 45px;
    line-height: 42px;
    padding-left: 8px;
    box-sizing: border-box;
    flex:1;
  }
  .itm .itm-num,.itm .emt {
    flex:0.5;
    padding:0;
  }
  .itm .itm-snum{
    flex:2;
  }
  .itm .itm-apply{
    padding:0;
  }
  .itm .itm-time{
    flex:3;
  }
  .itm .itm-stime{
    flex:2;
    text-align: start;
  }
  .itm .itm-cname{
    flex:2;
  }
  .itm .apply-btn {
    border: none;
    display: inline-block;
    width: 56px;
    height: 28px;
    border-radius: 3px;
    padding: 0px 8px 2px;
    margin-bottom: 10px;
    background-color: #253a73;
    color: white;
    cursor: pointer;
  }
  .itm .apply-btn:hover {
    background-color: #1e2f5d;
  }
  .itm-notice {
    overflow: auto;
    height: 39px;
    line-height: 36px;
    background-color: #ecf4fc;
    font-size: 13px;
    font-weight: 400;
    position: relative;
    padding-left: 40px;
  }
  .itm-notice i {
    position: absolute;
    left: 0;
    top: 8px;
    margin: 2px 5px 0 15px;
    line-height: 20px;
    color: #39abd4;
    font-size: 20px;
  }
  .itm-notice em {
    font-style: normal;
    font-weight: 700;
    font-size: inherit;
    color: #fe842f;
  }
  .itm:first-child {
    background-color: #f2f5fc;
    text-align: left;
    font-size: 14px;
    font-weight: 500;
    text-align: center;
  }
  .itm:first-child:hover {
    background-color: #f2f5fc;
  }
  .spare-itm a {
    background-color: #e1f4c3;
  }
  .spare-itm:hover a {
    background-color: #ffffff !important;
  }
  .selected-itm {
    height: 32px;
    border-bottom: 1px solid #ddd;
  }
  .selected-itm a {
    float: left;
    height: 31px;
    line-height: 31px;
    padding-left: 8px;
    box-sizing: border-box;
    background-color: rgb(250, 250, 250);
  }
</style>