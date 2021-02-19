<template>
  <div class="content-wrapper">
    <notice-modal v-if="modal" 
    @hideModal="hideModal"
    @home="$emit('home')"></notice-modal>
    <notice-content></notice-content>
  </div>
</template>

<script>
import NoticeModal from "../shared/NoticeModal.vue"; 
import NoticeContent from  "../shared/NoticeContent.vue";

export default {
  data(){
      return {
          modal:true
      }
  }, 
  created(){
      this.modal = true;
  },
  components: {
    NoticeModal,
    NoticeContent,
  },
  methods : {
      hideModal(){
          this.modal = false;
      }
  }
};
</script>

<style>
</style>