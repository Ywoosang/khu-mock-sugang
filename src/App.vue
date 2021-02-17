<template>
<span :class="{'totalWrapper':!home}">
  <register-page v-bind:timeLimit="timeLimit" @timeOver="renderHome" @home="renderHome" v-if="!home"></register-page>
  <home-page @register="startTest"  v-else></home-page>
</span>
</template>

<script>
import RegisterPage from "./components/RegisterPage.vue";
import HomePage from "./components/HomePage.vue";
export default {
  data(){
    return {
      timeLimit : 10,
      home : true,
    }
  },
  methods :{
    renderHome(){
      this.timeLimit =0; 
      this.home= true; 
    },
    startTest(){
      const timmer = setInterval(()=>{
        this.timeLimit-- 
      },1000)
      if(this.timeLimit==0){
        clearInterval(timmer);
        // 사전 오류 방지
        this.timeLimit=0; 
      }
      this.home=false;
    }
  },
  components:{
    "register-page": RegisterPage,
    "home-page" : HomePage,
  },
}
</script>

<style>
</style>