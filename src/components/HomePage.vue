<template>
  <div class="main">
    <div class="wrap-loader" style="display: none;"><span class="loading-helper"></span>
        <div class="loader"></div>
        <div class="loading-text">Loading</div>
    </div>
    <span class="to-top"></span>
    <div class="header-login">
        <div class="control is-opened" title="메뉴닫기"></div>
        <div title="경희대학교 수강신청시스템">
            <img src="./logo2.png">
        </div>
    </div>
    <div class="container">
        <div class="contents">
            <form name="form" id="form" method="post">
                <div class="wrap-login">
                    <div>
                        <div class="login-box">
                            <div class="wrap-lang">
                                <input type="radio" id="radio1" name="lang" value="ko" checked=""><label
                                    for="radio1">Korean</label>
                                <input type="radio" id="radio2" name="lang" value="en"><label
                                    for="radio2">English</label>
                            </div>
                            <select id="schedule_cd" name="schedule_cd" onchange="fnReload();">
                                <option value="hakbu" selected="">학부 수강신청</option>
                            </select>
                            <input type="text" class="input-id" id="id" name="id" placeholder="학번 ( Student ID )">
                            <input type="password" class="input-pw" id="pwd" name="pwd" placeholder="비밀번호 ( Password )">
                            <button type="button" class="btn-login" id="btn_login">로그인</button>
                            <button type="button" class="btn-login-sub" onclick="firstPw();">최초 사용자 비밀번호 등록</button>

                            <div class="text-btn">
                                <span onclick="javascript:findID();">ID찾기 </span>
                                <span onclick="javascript:findPwd();">비밀번호 찾기 </span>
                            </div>
                            <div class="manual">
                                <p onclick="javascript:downLoadMenual('w');">
                                    <i class="manual-pc"></i>
                                    <span class="manual-text">PC용 매뉴얼 </span>
                                </p>
                                <p onclick="javascript:downLoadMenual('m');">
                                    <i class="manual-mobile"></i>
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
                                    <span class="btn-more" onclick="goNotice('hakbu');"></span>
                                </p>
                                <div class="time">
                                    <span>2021/02/16 05:32:04</span>
                                </div>
                            </div>
                        </div>
                        <div>
                            <h2>희망과목 수강신청<small>WishList</small></h2>
                            <div class="schedule">
                                <p>
                                    희망과목 수강 안내 <br> WishList Course Registration
                                    <span class="btn-more" onclick="goNotice('wish');"></span>
                                </p>
                                <div class="time">
                                    <span>2021/02/16 05:32:04</span>
                                </div>
                            </div>
                        </div>
                        <div>
                            <h2>계절학기 수강신청<small>Summer/Winter</small></h2>
                            <div class="schedule">
                                <p>
                                    계절학기 수강 안내 <br> Summer/Winter Course Registration
                                    <span class="btn-more" onclick="goNotice('sess');"></span>
                                </p>
                                <div class="time">
                                    <span>2021/02/16 05:32:04</span>
                                </div>
                            </div>
                        </div>
                        <div>
                            <h2>대학원 수강신청<small>Graduate school</small></h2>
                            <div class="schedule">
                                <p>
                                    대학원 수강 안내<br> Graduate Course Registration
                                    <span class="btn-more" onclick="goNotice('grad');"></span>
                                </p>
                                <div class="time">
                                    <span>2021/02/16 05:32:04</span>
                                </div>
                            </div>
                        </div>
                    </div>
                    <h1>공지사항<small>Notice</small></h1>
                    <div class="wrap-notice">
                        <div>
                            <p>소융튜브에서 자체 제작한 <em>모의수강신청 사이트</em>로<br>폰트/아이콘/레이아웃 등이 살짝 다를 수 있습니다</p>
                            <p><em>학부 수강신청</em>기능만 제공하므로 이외 링크는 접속이 불가능할 수 있습니다</p>
                            <p>사이트 소스코드는 <a href="https://github.com/Ywoosang/KHU-Sugang" target="_blank" rel="noopener noreferrer"> Ywoosang/KHU-Sugang</a>에서 확인할 수 있습니다 <br>별도 문의 필요시 깃허브에 등록된 <em>개인 메일주소</em>로 부탁드립니다.</p>
                            <p>오류 및 버그 문의는 <a href="https://github.com/Ywoosang/KHU-Sugang" target="_blank" rel="noopener noreferrer"> Ywoosang/KHU-Sugang/issues </a> 에 <em>이슈</em> 로 등록합니다
                             </p>
                             <p><em>2022년</em> 이후 제작자 <em>군대</em> 문제로 유지보수가 어려울 수 있습니다
                             </p>
                            <p><em>크롬</em> 브라우저에 최적화 되어있습니다
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
        <div id="message" title="알림(notice)" style="display:none;z-index:2;">
            <p class="alert-warning"><span id="msg"></span></p>
        </div>
        <div id="retake" title="재수강 대상 과목조회" style="display:none;"></div>
        <div id="macro" title="매크로 방지용 키입력" style="display:none;"></div>
        <div id="switDialog" title="착오자 내역" style="display:none;"></div>
    </div>
    <div class="nav login">
        <div class="login" onclick="fnLogin('');" style="cursor:pointer">로그인</div>
        <div class="wrap-menu">
            <ul>
                <li class="notice" onclick="fnLoad(urlCoreNotice,'this');">
                    <img src="./icon-notice.png">
                    <span class="menu-kor">공지사항</span>
                </li>
                <li onclick="fnLoad(urlCoreLectureList,'this');">
                    <img src="./icon-planning.png">
                    <span class="menu-kor">종합시간표 조회</span>
                </li>
                <li onclick="fnLogin('hakbu');">
                    <img src="./icon-subject.png">
                    <span class="menu-kor">희망과목내역</span>
                </li>
                <li onclick="fnLogin('hakbu');">
                    <img src="./icon-search.png">
                    <span class="menu-kor">수강신청내역</span>
                </li>
                <li class="registration" onclick="fnLogin('hakbu');">
                    <img src="./img/icon-registration.png">
                    <span class="menu-kor">수강신청</span>
                </li>
            </ul>
        </div>
    </div>
</div>
</template>

<script>
export default {

}
</script>

<style>

</style>