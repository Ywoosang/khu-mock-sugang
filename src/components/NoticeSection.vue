<template>
<div class="content-panel">
  <notice-content></notice-content>
  <notice-modal></notice-modal>
</div>
</template>

<script>
import NoticeModal from "./NoticeModal.vue"
import NoticeContent from "./NoticeContent.vue"
export default {
    components : {
        'notice-modal' : NoticeModal,
        'notice-content' : NoticeContent
    }

}
</script>

<style>
.content-panel {
    padding: 25px;
    padding-top: 15px;
    box-sizing: border-box;
    margin-top:85px;
    width: calc(100vw - 120px);
}
.select{
  overflow: hidden;
}
</style>