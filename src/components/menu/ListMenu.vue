<template>
   <div class="content-wrapper">
       <course-list v-bind:courseList="courseList" v-bind:listMenu="true"></course-list>
   </div>
</template>

<script>
import CourseList from '../shared/CourseList.vue'
export default {
  props : ['courseList'],
  components: { 
      CourseList 
    },
}
</script>

<style>

</style>