<template>
  <div class="select">
    <button @click="wishClick"  v-bind:class="[ defaultTab ? 'wish-selected' : 'not-selected']" class="tab">
      <img  v-if="defaultTab" class="waf" src="bg-tab-left.png" alt="" />수강희망과목
    </button>
    <button  @click="searchClick" v-bind:class="[ defaultTab ? 'not-selected' : 'search-selected' ]" class="tab" >
        <!-- hide 로 가리기 -->
      <img v-if="!defaultTab" class="saf" src="bg-tab-right.png" alt="" />개설강좌검색
    </button>
  </div>
</template>

<script>
// 클릭시 자체적으로 변경하고, 이벤트로 부모요소에 보내주기
export default {
  props : ['defaultTab'],
  data() {
    return {
      wishTab :true,
      searchTab : false,
      
    }
  },
  methods : {
    changeTab(){
      this.$emit('tab');
    },
    wishClick(){
      // 기존 값과 반대
      const newValue = !this.wishTab 
      // 선택되지 않은 상황이였다면
      if(newValue == true){
        this.changeTab(); 
        this.wishTab = true;
        this.searchTab = false; 
      }
    },
    searchClick(){
      const newValue = !this.searchTab 
       if(newValue == true){
        this.changeTab(); 
        this.searchTab = true; 
        this.wishTab = false;
      }
    }
  }
};
</script>

<style>
.select {
  height: 43px;
  border-bottom: 1px solid #b6985a;
  padding: -1px;
}
.tab{
    height:42px;
    padding: 0 20px;
    margin:0;
}
.tab-img {
  object-fit: contain;
}

/* 수강희망과목이 선택되었을때 */
.wish-selected,
.search-selected {
  background-color: #b6985a;
  color: white;
  font-weight: bold;
  border: 1px solid #ad883f;
  border-right: none;
  border-bottom: none;
  border-radius: 6px 6px 0 0;
  position: relative;
}
.wish-selected .waf {
  width: 18px;
  height: 43px;
  position: absolute;
  right: -18px;
  top: -1px;
}
.search-selected .saf {
  width: 18px;
  height: 43px;
  position: absolute;
  right: -13px;
  top: -1px;
}
/* 선택되지 않은 탭 */
.not-selected {
  background-color: #e1e1e1;
  color: #777777;
  font-weight: bold;
  border: 1px solid rgb(199, 199, 199);
  border-bottom: none;
  border-radius: 6px 6px 0 0;
}
</style>