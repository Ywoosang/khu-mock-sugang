<template>
  <div class="wish-content">
                    <div class="itb-wrapper">
                        <div class="itb wish-itms">
                            <div class="itm">
                                <a class="emt"></a>
                                <a class="itm-apply">수강신청</a>
                                <a class="itm-clf">구분</a>
                                <a class="itm-snum">학수번호-분반</a>
                                <a class="itm-cname">강좌명</a>
                                <a class="itm-grd">대상학년</a>
                                <a class="itm-znum">정원</a>
                                <a class="itm-zanum">잔여인원</a>
                                <a class="itm-stime">신청가능시간</a>
                                <a class="itm-gname">교수명</a>
                                <a class="itm-hakzum">학점</a>
                                <a class="itm-time">강의시간/강의실</a>
                                <a class="itm-isgub">이수구분</a>
                            </div>
                        </div>
                    </div>
                    <div class="itm-notice">
                        <a><i style="margin:0 5px 0 15px; color:#39ABD4; font-size:20px;"
                                class="fas fa-exclamation-circle">
                            </i>희망과목 정원 및 잔여인원은 조회하는 시점 기준 인원으로 실시간 변동되므로, <em>'새로고침'</em> 또는 <em>'수강신청'</em> 재클릭시 조회
                            인원은
                            달라질 수 있습니다.</a>
                    </div>
                </div> 
</template>

<script>
export default {

}
</script>

<style>
.itb-wrapper{
    border: 1px solid rgb(236, 236, 236);
    width: inherit;
    overflow:auto;
}
.itb-exp{
    height: 47px;
}
.itb{
    padding-top: 1px;
    border-top:1px solid rgba(61, 177, 255, 0.472);
    width: 1731px;
}
/* 아이템 */
.itm{
    font-size: 12px;
    height: 45px;
    z-index: 1001;
    border-bottom: 1px solid rgba(221, 221, 221);
    text-align: center;
}
.itm:last-child{
    margin-bottom: 35px;
}
.itm a{
    float: left;
    height: 45px;
    line-height: 45px;
    padding-left: 8px;
    box-sizing: border-box;
}
.itm .itm-num{
    width: 41px;
}
.itm .itm-apply{
    width: 100px;
}
.itm .apply-btn{
    display: inline-block;
    width: 56px;
    height: 28px;
    border-radius: 3px;
    padding : 0px 8px 2px;
    background-color: #253A73;
    color: white;
}
.itm .apply-btn:hover{
    background-color: #1e2f5d;
}
.itm .itm-clf,.itm .itm-snum,.itm .itm-stime{
    width: 100px;
}
.itm .itm-cname,.itm .itm-time{
    width:250px;
}
.itm .itm-grd,.itm .itm-znum,.itm .itm-zanum,.itm .itm-hakzum
,.itm .itm-isgub{
    width: 60px;
}
.itm .itm-gname,.itm .itm-lang{
    width:120px;
}
.itm .itm-isgub{
    width: 80px; 
}
.itm .itm-time{
    text-align: start;
}
.itm .itm-special{
    width:160px;
}
.itm .emt{
    width: 41px;
}
/* 아래 문구  */
.itm-notice{
    overflow:auto;
    height: 39px;
    line-height: 36px;
    background-color: #ECF4FC;
    font-size: 13px;
    font-weight: 400;
    position: relative;
    padding-left: 40px;
}
.itm-notice i{
    position: absolute;
    left:0;
    top: 8px;
    margin:2px 5px 0 15px;
    line-height: 20px;
    color:#39ABD4; 
    font-size:20px;
}
.itm-notice em{
    font-style: normal;
    font-weight: 700;
    font-size: inherit;
    color: #fe842f;
}
/* 표 헤드 부분 */
.itm:first-child{
    background-color: #F2F5FC;
    text-align: left;
    font-size: 14px;
    font-weight: 500;
    text-align: center;
}
.itm:first-child:hover{
    background-color: #F2F5FC;
}
/* 예비과목일 경우 클래스 추가해주기 */
.spare-itm a{ 
    background-color: #E1F4C3;
}
.spare-itm:hover a{
    background-color: #ffffff !important;
}
/* 신청한 경우  클래스 추가해주기 */
.selected-itm{
    height: 32px;
    border-bottom: 1px solid #ddd;
}
.selected-itm a{
    float: left;
    height: 31px;
    line-height: 31px;
    padding-left: 8px;
    box-sizing: border-box;   
    background-color: rgb(250, 250, 250);
}
</style>