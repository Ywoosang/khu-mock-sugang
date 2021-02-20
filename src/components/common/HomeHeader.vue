<template>
 <header  class='header-login'>
       <div class="control is-opened" title="메뉴닫기" style="cursor:not-allowed;"></div>
        <div class="header-logo" @click="refresh" title="경희대학교 수강신청시스템">
            <img src="logo2.png">
        </div>
 </header>
</template>

<script>

export default {
    methods:{
        refresh(){
            location.reload();
        }
    }

}
</script>

<style>
.header-logo {
    cursor: pointer;
}
</style>