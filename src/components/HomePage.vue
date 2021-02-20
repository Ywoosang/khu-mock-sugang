<template>
    <div class="container">
        <div class="contents">
            <form name="form" id="form" method="post">
                <div class="wrap-login" :style="{ 'background': 'url(bg-login.jpg) no-repeat center 0' }">
                    <div>
                        <div class="login-box">
                            <div class="wrap-lang">
                                <input type="radio" id="radio1" name="lang" value="ko" checked=""><label
                                    for="radio1">Korean</label>
                                <!-- <input type="radio" id="radio2" name="lang" value="en"><label
                                    for="radio2">English</label> -->
                            </div>
                            <select :style="{ 'background-image': 'url(bg-select.png) no-repeat center 0' }" id="schedule_cd" name="schedule_cd" disabled>
                                <option>학부 수강신청</option>
                            </select>
                            <input v-model="fakeId" :style="{ 'background': 'url(icon-id.png) no-repeat 10px center' }" type="text" class="input-id" id="id" name="id" placeholder="학번 ( Student ID )">
                            <input v-model="fakePwd" :style="{ 'background': 'url(icon-pw.png) no-repeat 11px center' }" type="password" class="input-pw" id="pwd" name="pwd" placeholder="비밀번호 ( Password )">
                            <button @click="startTest" style="cursor:pointer;" type="button" class="btn-login" id="btn_login">모의 수강신청 시작</button>
                            <button style="cursor:not-allowed;" type="button" class="btn-login-sub">최초 사용자 비밀번호 등록</button>

                            <div class="text-btn">
                                <span style="cursor:not-allowed;">ID찾기 </span>
                                <span style="cursor:not-allowed;">비밀번호 찾기 </span>
                            </div>
                            <div class="manual">
                                <p style="cursor:not-allowed;">
                                    <i :style="{ 'background-image': 'url(icon-pc.png)' }" class="manual-pc"></i>
                                    <span class="manual-text">PC용 매뉴얼 </span>
                                </p>
                                <p style="cursor:not-allowed;">
                                    <i :style="{ 'background-image': 'url(icon-mobile.png)' }" class="manual-mobile"></i>
                                    <span class="manual-text">모바일용 매뉴얼 </span>
                                </p>
                            </div>
                        </div>
                    </div>
                </div>
            </form>

            <div class="login-contents">
                <div>
                    <h1>수강신청 일정<small>Course Registration Schedule</small></h1>
                    <div class="wrap-schedule">
                        <div>
                            <h2>학부 수강신청<small>Undergraduate</small></h2>
                            <div class="schedule">
                                <p>
                                    학부 수강 안내 <br> Course Registration
                                    <span style="cursor:not-allowed;" :style="{ 'background': 'url(btn-more-blue.png) no-repeat center center' }" class="btn-more"></span>
                                </p>
                                <div :style="{ 'background': 'url(icon-clock.png) no-repeat left center' }" class="time">
                                    <span>2021/02/16 05:32:04</span>
                                </div>
                            </div>
                        </div>
                        <div>
                            <h2>희망과목 수강신청<small>WishList</small></h2>
                            <div class="schedule">
                                <p>
                                    희망과목 수강 안내 <br> WishList Course Registration
                                    <span style="cursor:not-allowed;" :style="{ 'background': 'url(btn-more-blue.png) no-repeat center center' }" class="btn-more"></span>
                                </p>
                                <div :style="{ 'background': 'url(icon-clock.png) no-repeat left center' }" class="time">
                                    <span>2021/02/16 05:32:04</span>
                                </div>
                            </div>
                        </div>
                        <div>
                            <h2>계절학기 수강신청<small>Summer/Winter</small></h2>
                            <div class="schedule">
                                <p>
                                    계절학기 수강 안내 <br> Summer/Winter Course Registration
                                    <span style="cursor:not-allowed;" :style="{ 'background': 'url(btn-more-blue.png) no-repeat center center' }" class="btn-more"></span>
                                </p>
                                <div :style="{ 'background': 'url(icon-clock.png) no-repeat left center' }" class="time">
                                    <span>2021/02/16 05:32:04</span>
                                </div>
                            </div>
                        </div>
                        <div>
                            <h2>대학원 수강신청<small>Graduate school</small></h2>
                            <div class="schedule">
                                <p>
                                    대학원 수강 안내<br> Graduate Course Registration
                                    <span style="cursor:not-allowed;" :style="{ 'background': 'url(btn-more-blue.png) no-repeat center center' }" class="btn-more"></span>
                                </p>
                                <div :style="{ 'background': 'url(icon-clock.png) no-repeat left center' }" class="time">
                                    <span>2021/02/16 05:32:04</span>
                                </div>
                            </div>
                        </div>
                    </div>
                    <h1>공지사항<small>Notice</small></h1>
                    <div class="wrap-notice">
                        <div>
                            <p :style="{ 'background': 'url(bullet-blue.png) no-repeat 0 7px' }"><em>소융튜브</em> 에서 자체 제작한 <em>모의수강신청 사이트</em>로<br>폰트/아이콘/레이아웃 등이 살짝 다를 수 있습니다</p>
                            <p :style="{ 'background': 'url(bullet-blue.png) no-repeat 0 7px' }"><em>학부 수강신청</em>기능만 제공하므로 이외 링크는 접속이 불가능할 수 있습니다</p>
                            <p :style="{ 'background': 'url(bullet-blue.png) no-repeat 0 7px' }">사이트 소스코드는 <a href="https://github.com/Ywoosang/KHU-Sugang" target="_blank" rel="noopener noreferrer"> Ywoosang/KHU-Sugang</a>에서 확인하실 수 있습니다 <br>개발 및 기타사항등 별도 문의 필요시 깃허브에 등록된 <em>개인 메일주소</em>로 부탁드립니다.</p>
                            <p :style="{ 'background': 'url(bullet-blue.png) no-repeat 0 7px' }">오류 및 개선 문의는 <a href="https://github.com/Ywoosang/KHU-Sugang" target="_blank" rel="noopener noreferrer"> Ywoosang/KHU-Sugang/issues </a> 에 <em>이슈</em> 로 등록합니다
                             </p>
                             <p :style="{ 'background': 'url(bullet-blue.png) no-repeat 0 7px' }"><em>2022년</em> 이후 제작자 <em>군대</em> 문제로 유지보수가 어려울 수 있습니다
                             </p>
                            <p :style="{ 'background': 'url(bullet-blue.png) no-repeat 0 7px' }"><em>크롬</em> 브라우저에 최적화 되어있습니다</p>
                        </div>
                     
                    </div>
                </div>
            </div>
            <div class="footer">
                <div>
                    서울캠퍼스 02447 서울특별시 동대문구 경희대로 26 l 국제캠퍼스 17104 경기도 용인시 기흥구 덕영대로 1732 l 광릉캠퍼스 12001 경기도 남양주시 진접읍 광릉수목원로
                    195<br>
                    COPYRIGHT © KYUNG HEE UNIVERSITY. ALL RIGHT RESERVED.
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data(){
        return {
            fakeId : '',
            fakePwd : ''
        }
    },
    methods: {
        // 비동기 병렬 순차처리 
        startTest(){
            Array.prototype.asyncForEach = async function(callback){
                for(let index=0; index<this.length; index++){
                    // promise 를 반환하는 콜백함수 가정
                    await callback(this[index],index,this)
            }};
            const inputEffect = (string,delay) =>{
                string.split("").asyncForEach((el)=>{
                    return new Promise((resolve)=>{
                    setTimeout(()=>{
                        delay ===100 ? this.fakeId +=el : this.fakePwd+=el;
                        resolve();
                    },delay);
                }); });
            }
            inputEffect("2020109999",100);
            inputEffect( "khu123456789@@",50);
        },
    },
    watch : {
        fakeId(){
            if(this.fakeId.length==10) {
                setTimeout(()=>{
                     this.$emit('register');
                },500)
            }
        }
    }}; 
</script>

<style>
html, body, * {
    margin: 0;
    padding: 0;
    font-size: 13px;
    color: #333;
    line-height: 1.4;
    box-sizing: border-box;
    outline: 0 none;
}
h1 {
    display: inline-block;
    width: 100%;
    padding-left: 2px;
    font-size: 18px;
    font-weight: 700;
    color: #0d0d0d;
}
link {
    display: none;
}
*, *:after, *:before {
    box-sizing: border-box;
}
em {
    font-style: normal;
    font-weight: bold;
    font-size: inherit;
    color: #fe842f;
}

.main {
    margin-left: 120px;
    height: 100%;
    transition: all .4s;
}
.main>.wrap-loader {
    position: fixed;
}
.wrap-loader {
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    z-index: 2;
    text-align: center;
    background: rgba(73,74,77,0.4);
    transition: all 250ms linear;
}
.wrap-loader .loading-helper {
    display: inline-block;
    height: 100%;
    vertical-align: middle;
    margin-top: 50px;
    margin-left: 50px;
}
span, a {
    display: inline-block;
    font-size: inherit;
    font-weight: inherit;
    color: inherit;
}
.wrap-loader .loader {
    position: relative;
    display: inline-block;
    text-indent: -9999999em;
    border-radius: 100%;
    width: 80px;
    height: 80px;
    margin-top: 5px;
    border-top: 2px solid transparent;
    border-right: 2px solid #253a73;
    border-bottom: 2px solid transparent;
    border-left: 2px solid #253a73;
    -webkit-animation: load 1.0s infinite linear;
    animation: load 1.0s infinite linear;
}
.wrap-loader .loading-text {
    position: relative;
    left: -65px;
    top: -33px;
    display: inline-block;
    margin: 0 auto;
    font-weight: bold;
    font-size: 12px;
    color: #253a73;
    text-align: center;
    text-transform: uppercase;
    opacity: 0;
    animation: loading-text 1.5s linear 0s infinite normal;
}
.to-top {
    display: none;
    position: fixed;
    z-index: 1;
    right: 20px;
    bottom: 20px;
    width: 32px;
    height: 32px;
    border-radius: 16px;
    /* background:   url(./img/icon-top.png) no-repeat 50% 50%; */
    cursor: pointer;
}
/* 헤더부분  */
.main .header-login {
    position:relative;
    min-width: 1260px;
    width: calc(100vw - 120px);
    height: 94px;
    padding: 0 30px;
    background-color: #113769;
    transition: all .2s;
}
.main .header-login .control {
    position: absolute;
    top: 0;
    left: 0px;
    width: 17px;
    height: 94px;
    margin: 0;
    background: #253a73;
    transition: all .4s;
}
.main .header-login .control::before {
    content: "";
    position: absolute;
    top: 44px;
    width: 6px;
    height: 6px;
    border: solid #fff;
    border-width: 1px 1px 0 0;
    background: transparent;
    transition: all .4s;
    display: flex;
    flex-direction: column;
}
.main .header-login>div {
    display: flex;
    align-items: center;
    position: relative;
    height: 100%;
    margin: 0 auto;
}
.main .header-login .control.is-opened:before {
    left: 7px;
    transform: rotate(
-135deg
);
}

/* 메인 부분 시작 */
.container {
    min-width: 1260px;
    width: calc(100vw - 120px);
    height: calc(100% - 60px);
    overflow: auto;
    transition: all .4s;
}
.container .contents {
    overflow: hidden;
    min-height: calc(100% - 35px);
    padding-bottom: 0;
}

/* 로그인창 */
.wrap-login {
    position: relative;
    overflow: hidden;
    width: 100%;
    height: 535px;
    /* background: url("./img/bg-login.jpg") no-repeat center 0; */
    box-sizing: border-box;
}
.wrap-login>div {
    position: relative;
    width: 1140px;
    margin: 0 auto;
}
.wrap-login>div .login-box {
    position: relative;
    float: right;
    width: 330px;
    margin-top: 20px;
    padding: 25px 30px 30px;
    background: #fff;
    box-sizing: border-box;
}
.wrap-login>div .login-box .wrap-lang {
    margin-bottom: 18px;
    text-transform: uppercase;
}
input[type="radio"], input[type="checkbox"] {
    margin-left: 0;
    width: 18px;
    height: 18px;
    background: transparent;
    vertical-align: text-top;
    display: none;
}
input[type="radio"]+label, input[type="checkbox"]+label {
    display: inline-block;
    position: relative;
    height: 18px;
    margin: 2px 0;
    padding: 0 10px 0 25px;
    transition: all .2s;
}
input[type="radio"]+label:before, input[type="checkbox"]+label:before {
    content: "";
    border-color: #18a7b8;
    border-radius: 10px;
    position: absolute;
    top: 0;
    left: 0;
    width: 18px;
    height: 18px;
    background: #fff;
    border: 1px solid #ccc;
    transition: all .2s;
}
input[type="radio"]:checked+label:after, input[type="checkbox"]:checked+label:after {
    content: "";
    position: absolute;
    top: 4px;
    left: 4px;
    width: 10px;
    height: 10px;
    border-radius: 1rem;
    background: #18a7b8;
    transition: all .2s;
}
input[type="text"], input[type="password"] {
    width: 100%;
    font-family: "Segoe UI","맑은 고딕","Malgun Gothic","애플 SD 산돌고딕 Neo","Apple SD Gothic Neo",sans-serif;
    font-weight: normal;
    font-size: 13px;
    letter-spacing: -.5px;
    border: 1px solid #b9b9b9;
    border-radius: 0;
    appearance: none;
    border-color: #ccc;
    padding: 0 5px;
}

.wrap-login>div .login-box select {
    height: 40px;
    margin-bottom: 15px;
    padding-left: 10px;
    background-color: #f2f7fc;
    background-position: right 15px top 50%;
}
select {
    width: 100%;
    height: 34px;
    font-family: "Segoe UI","맑은 고딕","Malgun Gothic","애플 SD 산돌고딕 Neo","Apple SD Gothic Neo",sans-serif;
    font-weight: normal;
    font-size: 13px;
    line-height: 34px;
    letter-spacing: -.5px;
    border: 1px solid #b9b9b9;
    border-radius: 0;
    appearance: none;
    box-sizing: border-box;
    border-color: #ccc;
    padding: 0 26px 2px 5px;
    /* background-image: url(./img/bg-select.png); */
    background-repeat: no-repeat;
    background-position: right 8px top 50%;
    line-height: 28px;
}
select option {
    padding-left: 5px;
}
/* .wrap-login>div .login-box input.input-id {
    background: url(./img/icon-id.png) no-repeat 10px center;
} */
/* .wrap-login>div .login-box input.input-pw {
    background: url(./img/icon-pw.png) no-repeat 11px center;
} */
.wrap-login>div .login-box button.btn-login {
    width: 100%;
    height: 50px;
    margin-top: 10px;
    margin-bottom: 10px;
    background-color: #113769;
    border-radius: 6px;
    border: 0;
    font-size: 18px;
    font-weight: bold;
    color: #fff;
    text-align: center;
}
.wrap-login>div .login-box button.btn-login-sub {
    width: 100%;
    height: 40px;
    background-color: #a6a39d;
    border-radius: 6px;
    border: 0;
    font-size: 14px;
    color: #fff;
    text-align: center;
}
.wrap-login>div .login-box .text-btn {
    display: -webkit-flex;
    display: -ms-flexbox;
    display: -webkit-box;
    display: flex;
    margin: 15px 0;
}
.wrap-login>div .login-box .text-btn span:first-child{
    border:none;
} 
.wrap-login>div .login-box .text-btn span {
    -webkit-flex: 1 1 0;
    -ms-flex: 1 1 0;
    flex: 1 1 0;
    max-width: 100%;
    min-width: 0;
    width: auto;
    text-align: center;
    cursor: pointer;
    border-left: 1px solid #e6e6e6;
}
.wrap-login>div .login-box .manual {
    display: flex;
}
.wrap-login>div .login-box .manual>p:first-child {
    margin-left: 0;
}
.wrap-login>div .login-box .manual>p {
    flex: 1 1 0;
    max-width: 100%;
    min-width: 0;
    width: auto;
    height: 90px;
    background: #f3f3f3;
    font-size: 15px;
    font-weight: bold;
    color: #113769;
    text-align: center;
    cursor: pointer;
    margin-left: 1px;
}
.wrap-login>div .login-box .manual>p:hover {
    background: #e6e6e6;
}

/* 인풋박스 */
.wrap-login>div .login-box input {
    float: left;
    height: 40px;
    line-height: 40px;
    margin-bottom: 10px;
    padding-left: 36px;
}
/* 매뉴얼 아이콘 */
/* .wrap-login>div .login-box .manual>p i.manual-pc {
    background-image: url(./img/icon-pc.png);
} */
.wrap-login>div .login-box .manual>p i {
    display: inline-block;
    width: 30px;
    height: 30px;
    margin: 18px 0 3px;
    border-radius: 15px;
    background-color: #113769;
    background-repeat: no-repeat;
    background-position: 50% 50%;
}
/* .wrap-login>div .login-box .manual>p i.manual-mobile {
    background-image: url(./img/icon-mobile.png);
} */
.wrap-login>div .login-box .manual>p span {
    width: 100%;
    line-height: 1;
    letter-spacing: -1px;
}
.login-contents {
    width: 100%;
    padding: 45px 0 0;
    box-sizing: border-box;
}
.login-contents>div {
    position: relative;
    width: 1140px;
    margin: 0 auto;
}
.login-contents h1 {
    margin-bottom: 20px;
    font-size: 26px;
    font-weight: normal;
    letter-spacing: -2px;
    word-spacing: -1px;
}
.login-contents h1 small {
    margin-left: 10px;
    font-size: 16px;
    font-weight: normal;
    color: #666;
    letter-spacing: 0;
    word-spacing: 0;
}

.login-contents .wrap-schedule {
    display: flex;
    align-items: stretch;
    margin-bottom: 50px;
}
.login-contents .wrap-notice {
    display: flex;
    align-items: stretch;
    margin-bottom: 60px;
}
.login-contents .wrap-notice>div {
    -webkit-flex: 1 1 0;
    -ms-flex: 1 1 0;
    flex: 1 1 0;
    max-width: 100%;
    min-width: 0;
    position: relative;
    margin-left: 20px;
    padding: 38px 30px;
    border: 1px solid #dedede;
    background: #fff;
    box-sizing: border-box;
}
.login-contents .wrap-notice>div p {
    margin-bottom: 10px;
    padding: 0 0 0 12px;
    /* background: url(./img/bullet-blue.png) no-repeat 0 7px; */
    font-size: 14px;
    line-height: 22px;
    letter-spacing: -1px;
    box-sizing: border-box;
}
.login-contents .wrap-schedule>div {
    flex: 1 1 0;
    max-width: 100%;
    min-width: 0;
    position: relative;
    margin-left: 40px;
    box-sizing: border-box;
}
.login-contents .wrap-schedule>div:first-child{
    margin-left :20px;
}
.login-contents .wrap-schedule>div h2 {
    position: relative;
    width: calc(100% - 12px);
    height: 30px;
    margin-bottom: 20px;
    padding: 2px 20px 0;
    background: #70bded;
    font-size: 14px;
    color: #fff;
    letter-spacing: -1px;
    word-spacing: -1px;
    box-sizing: border-box;
}
.login-contents .wrap-schedule>div h2 small {
    margin-left: 5px;
    font-size: 13px;
    font-weight: normal;
    color: rgba(255,255,255,0.6);
    letter-spacing: 0;
    word-spacing: 0;
}
.login-contents .wrap-schedule>div h2:before {
    content: "";
    display: inline-block;
    height: 100%;
    vertical-align: middle;
    font-size: 0;
}
.login-contents .wrap-schedule>div h2:after {
    content: "";
    position: absolute;
    top: 0;
    right: -12px;
    width: 0;
    height: 0;
    border-right: 12px solid transparent;
    border-top: 15px solid #70bded;
    border-bottom: 15px solid #70bded;
}
.login-contents .wrap-schedule>div .schedule {
    position: relative;
    float: left;
    width: 100%;
    height: 110px;
    padding-left: 20px;
    border-left: 1px solid #70bded;
    box-sizing: border-box;
}
.login-contents .wrap-schedule>div .schedule p {
    font-size: 18px;
    line-height: 22px;
}
.login-contents .wrap-schedule>div .schedule .btn-more {
    display: inline-block;
    position: relative;
    top: 5px;
    width: 60px;
    height: 22px;
    /* background: url(./img/btn-more-blue.png) no-repeat center center; */
    cursor: pointer;
}
.login-contents .wrap-schedule>div .schedule .time {
    position: absolute;
    left: 20px;
    bottom: 2px;
    padding-left: 18px;
    /* background: url(./img/icon-clock.png) no-repeat left center; */
    font-size: 13px;
    line-height: 12px;
    color: #999;
    box-sizing: border-box;
}
</style>