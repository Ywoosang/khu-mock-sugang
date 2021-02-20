<template>
    <div class="container">
<!-- props 로 sidebar 에서 선택 바꿈 이벤트가 내려오면 탭 바꿔주기-->
        <notice-menu 
         @home="$emit('home')"
         v-if="isNoticeMenu"></notice-menu>
        <wish-menu v-if="isWishMenu"></wish-menu>
        <list-menu v-bind:courseList="courseList" v-if="isListMenu"></list-menu>
        <time-limit v-if="isRegisterMenu && timeLimit>0" v-bind:timeLimit="timeLimit"></time-limit>
        <!-- timeLimit 보고 모달 띄우기 -->
        <register-menu @reset="resetCourses" @renewal="renewalCourse" @home="$emit('home')" v-bind:Courses="courseList" v-if="isRegisterMenu && timeLimit<=0"></register-menu>
        <course-footer></course-footer>
    </div>
</template>

<script>
import ListMenu from './menu/ListMenu.vue';
import NoticeMenu from './menu/NoticeMenu.vue';
import RegisterMenu from './menu/RegisterMenu.vue';
import WishMenu from './menu/WishMenu.vue';
import TimeLimit from './common/TimeLimit.vue';
import CourseFooter from './common/CourseFooter.vue';

export default {
    props : ['timeLimit','menu'],
    data(){
        return {
            courseList : [],
        }
    },
    components : {
        'list-menu' : ListMenu,
        'notice-menu' : NoticeMenu,
        'register-menu' : RegisterMenu,
        'wish-menu' : WishMenu,
        'time-limit' : TimeLimit,
        CourseFooter 
    },
    computed: {
        isNoticeMenu(){
            if(this.menu=='noticeMenu') return true;
            return false ; 
        },
        isWishMenu(){
            if(this.menu=='wishMenu') return true;
            return false;
        },
        isListMenu(){
            if(this.menu=='listMenu') return true;
            return false; 
        },
        isRegisterMenu(){
            if(this.menu=='registerMenu') return true;
            return false; 
        }
    },
    methods : {
        renewalCourse(courses){
            this.courseList=courses;
        },
        resetCourses(){
            this.courseList=[];
        }
    }
}
</script>

<style>

</style>