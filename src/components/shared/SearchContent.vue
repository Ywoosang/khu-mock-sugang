<template>
  <div>
    <div class="pnl-search">
      <table>
        <colgroup>
          <col width="60px;" />
          <col width="15%" />
          <col width="80px;" />
          <col width="15%" />
          <col width="80px;" />
          <col width="15%" />
          <col width="100px;" />
          <col width="15%" />
        </colgroup>
        <tbody>
          <tr style="margin-bottom:10px;">
            <th id="hide4">대학</th>
            <td>
              <select
                :style="{ 'background-image': 'url(/bg-select.png)' }"
                name="p_daehak"
                id="p_daehak"
                style="width: 100%"
              >
                <option value="A01008">문과대학</option>
                <option value="A00400">법과대학</option>
                <option value="A00422">정경대학</option>
                <option value="A01024">경영대학</option>
                <option value="A00681">호텔관광대학</option>
                <option value="A01043">이과대학</option>
                <option value="A00556">생활과학대학</option>
                <option value="A00585">의과대학</option>
                <option value="A00613">한의과대학</option>
                <option value="A00622">치과대학</option>
                <option value="A00632">약학대학</option>
                <option value="A01074">간호과학대학</option>
                <option value="A00645">음악대학</option>
                <option value="A01085">미술대학</option>
                <option value="A01101">무용학부</option>
                <option value="A00874">자율전공학과</option>
                <option value="A04754">공과대학</option>
                <option value="A05091">전자정보대학</option>
                <option value="A07340" selected="">소프트웨어융합대학</option>
                <option value="A05346">응용과학대학</option>
                <option value="A05165">생명과학대학</option>
                <option value="A05366">국제대학</option>
                <option value="A04620">외국어대학</option>
                <option value="A05240">예술·디자인대학</option>
                <option value="A05297">체육대학</option>
                <option value="A10158">융합</option>
                <option value="A10259">후마니타스칼리지교육과정(서울)</option>
                <option value="A10258">후마니타스칼리지교육과정(국제)</option>
                <option value="A01179">기타(서울)</option>
                <option value="A05418">자연계열</option>
                <option value="A05522">기타(국제)</option>
              </select>
            </td>
            <th id="hide5">학과</th>
            <td>
              <select
                :style="{ 'background-image': 'url(/bg-select.png)' }"
                name="p_major"
                style="width: 100%"
              >
                <option value="A07337">
                  소프트웨어융합대학 소프트웨어융합학과 소프트웨어융합학
                </option>
                <option value="A07308">
                  소프트웨어융합대학 컴퓨터공학과 컴퓨터공학
                </option>
              </select>
            </td>
            <th id="hide6">강좌명</th>
            <td>
              <input   @keydown.space="keyPrevent"
                @keydown.enter="keyPrevent" type="text" placeholder="검색어 (Search Word)" />
            </td>
            <th id="hide10">언어구분</th>
            <td>
              <select
               :style="{ 'background-image': 'url(/bg-select.png)' }"
                name="p_lang"
                id="p_lang"
                style="width: 100%"
              >
                <option value="">---- All ----</option>
                <option value="1">영어</option>
                <option value="2">영어(부분)</option>
                <option value="3">제2외국어</option>
              </select>
            </td>
          </tr>
          <tr>
            <th id="hide7">요일</th>
            <td>
              <select
                :style="{ 'background-image': 'url(/bg-select.png)' }"
                name="p_day"
                style="width: 100%"
              >
                <option value="">- All -</option>
                <option value="2">월요일</option>
                <option value="3">화요일</option>
                <option value="4">수요일</option>
                <option value="5">목요일</option>
                <option value="6">금요일</option>
                <option value="7">토요일</option>
              </select>
            </td>
            <th id="hide8">수업시간</th>
            <td>
              <select
                :style="{ 'background-image': 'url(/bg-select.png)' }"
                name="p_time"
                id="p_time"
                style="width: 100%"
              >
                <option value="">- All -</option>
                <option value="0900">09:00</option>
                <option value="0930">09:30</option>
                <option value="1000">10:00</option>
                <option value="1030">10:30</option>
                <option value="1100">11:00</option>
                <option value="1130">11:30</option>
                <option value="1200">12:00</option>
                <option value="1230">12:30</option>
                <option value="1300">13:00</option>
                <option value="1330">13:30</option>
                <option value="1400">14:00</option>
                <option value="1430">14:30</option>
                <option value="1500">15:00</option>
                <option value="1530">15:30</option>
                <option value="1600">16:00</option>
                <option value="1630">16:30</option>
                <option value="1700">17:00</option>
                <option value="1730">17:30</option>
                <option value="1800">18:00</option>
                <option value="1825">18:25</option>
                <option value="1850">18:50</option>
                <option value="1900">19:00</option>
                <option value="1915">19:15</option>
                <option value="1930">19:30</option>
                <option value="1940">19:40</option>
                <option value="2005">20:05</option>
                <option value="2030">20:30</option>
                <option value="2035">20:35</option>
                <option value="2055">20:55</option>
                <option value="2100">21:00</option>
                <option value="2120">21:20</option>
                <option value="2125">21:25</option>
                <option value="2145">21:45</option>
                <option value="2150">21:50</option>
              </select>
            </td>
            <th id="hide9">교수명</th>
            <td>
              <input 
                @keydown.space="keyPrevent"
                @keydown.enter="keyPrevent"
              type="text" placeholder="검색어 (Search Word)" />
            </td>
            <th id="hide11">학수번호<br />분반</th>
            <td>
              <input
                v-model="courseNum"
                @keydown.space="keyPrevent"
                @keydown.enter="keyPrevent"
                type="text"
                class="courseINumber"
                placeholder="검색어 (Search Word)"
              />
            </td>
          </tr>
        </tbody>
      </table>
      <div class="buttonset">
        <button style="border:none;"
          @click="searchCourse"
          :style="{ 'background-image': 'url(search.png)' }"
          class="btn-search"
        >
          조회
        </button>
      </div>
    </div>


    <div class="search-content">
      <div class="itb-wrapper">
        <div class="itb search-itms">
          <div class="itm">
            <a class="emt"></a>
            <a class="itm-apply">수강신청</a>
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
            <a class="itm-lang">언어구분</a>
            <a class="itm-special">특이사항</a>
          </div>
          <div v-if="loading" class="loading">
            <div class="loading-bar">Loading ...</div>
          </div>
          <div v-for="num in contents" v-bind:key="num" class="itm">
            <a class="emt">{{ num }}</a>
            <a class="itm-apply"><button @click="courseApply" class="apply-btn">신청</button></a>
            <a class="itm-snum">ADD123-01</a>
            <a style="text-align:left;" class="itm-cname">강좌 {{ num }}</a>
            <a class="itm-grd">0</a>
            <a class="itm-znum">30</a>
            <a class="itm-zanum">8</a>
            <a class="itm-stime"></a>
            <a class="itm-gname">교수{{ num }}</a>
            <a class="itm-hakzum">3</a>
            <a class="itm-time">월 10:30-13:00 (강의실)</a>
            <a class="itm-isgub"></a>
            <a class="itm-lang">영어(부분)</a>
            <a class="itm-special"></a>
          </div>
        </div>
      </div>
      <div class="itm-notice">
        <a
          ><i
            style="margin: 0 5px 0 15px; color: #39abd4; font-size: 20px"
            class="fas fa-exclamation-circle"
          >
          </i
          >이수구분 : 11 전공기초, 04 전공필수, 05 전공선택, 06 교직과, 14
          중핵교과, 15 배분이수교과, 16 기초교과, 17 자유이수, 20 교직전선, 24
          계절학기전공필수, 27 계절학기전공기초, 08
          자유선택교과[배움학점제,군사학,취업스쿨,학점교류 과목등]</a
        >
      </div>
    </div>
  </div>
</template>

<script>

export default {
  props: ["isSearch"],
  data() {
    return {
      loading: true,
      contents: [],
      courseNum :''
    };
  },
  created() {
    setTimeout(() => {
      this.loading = false;
      this.contents = this.range(10);
    }, 1500);
  },
  methods: {
     range: (l) => Array.apply(null, { length: l }).map((_,index)=> index+1),
    searchCourse() {
        this.contents = [] 
        this.loading = true;
        setTimeout(() => {
          this.loading = false; 
          this.contents = this.courseNum.trim() === '' ? this.range(10) : this.range(1);
          this.$emit('searchNum',this.contents.length)
          return; 
        },3100);
    },
    keyPrevent(e){
      alert('매크로 방지를 위해 엔터키와 스페이스바 키는 사용하실 수 없습니다.')
      e.returnValue = false;

    },
     courseApply(num){
        setTimeout(()=>{
            this.$emit('apply',num); 
        },1500)
    }
  },
};
</script>

<style>
.pnl-search {
    margin-top: 15px;
    position: relative;
    margin-bottom: 15px;
    padding: 11px 20px;
    border-radius: 6px;
    border: 1px solid #e5e5e5;
}
.pnl-search table {
    width: calc(100% - 100px);
    max-width: 1300px;
    table-layout: fixed;
    border-spacing: 0;
    position: static;
    display: table;
    border-collapse: separate;
    text-indent: initial;
    border-color: grey;
}
.pnl-search td+th {
    padding-left: 25px;
}
.pnl-search th {
    padding: 0 0 2px;
    font-size: 12px;
    line-height: 1.1;
    word-spacing: -.5px;
    text-align: left;
    vertical-align: middle;
}
.pnl-search tbody {
    display: table-row-group;
    vertical-align: middle;
    border-color: inherit;
}
.pnl-search tr {
    display: table-row;
    vertical-align: inherit;
    border-color: inherit;
}
.pnl-search table th {
    position: relative;
    padding: 7px 3px 0 0;
    font-weight: 700;
    color: #4d4d4d;
    text-align: right;
    vertical-align: top;
}
.pnl-search table td {
    padding: 0 0 5px 5px;
}
.pnl-search select {
    outline: none;
    appearance: none;
    width: 100%;
    height: 34px;
    font-weight: 400;
    font-size: 13px;
    line-height: 34px;
    letter-spacing: -.5px;
    border: 1px solid #b9b9b9;
    border-radius: 0;
    box-sizing: border-box;
    border-color: #ccc;
    padding: 0 26px 2px 5px;
    background-repeat: no-repeat;
    background-position: right 8px top 50%;
    line-height: 28px;
}
.pnl-search input{
    width: 100%;
    height: 34px;
    font-weight: 400;
    font-size: 13px;
    line-height: 34px;
    letter-spacing: -.5px;
    border: 1px solid #b9b9b9;
    border-radius: 0;
    -moz-appearance: none;
    appearance: none;
    -webkit-box-sizing: border-box;
    box-sizing: border-box;
    border-color: #ccc;
    outline: none;
    padding: 0 5px;
}
.pnl-search button.btn-search {
    position:absolute;
    top: 12px;
    right: 20px;
    background-color: #444;
    border-color: #444;
    color: #fff;
    background-repeat: no-repeat;
    background-position: 12px 8px;
    padding-left: 32px;
    box-sizing: border-box;
    width: 70px;
    height: 34px;
    line-height: 34px;
    font-size: 13px;
    font-weight: 400;
    cursor: pointer;
    border-radius: 3px;
}
.loading {
  width: 100%;
  height: 400px;
  background-color: white;
  position: relative;
}
.loading .loading-bar {
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%);
  width: 83px;
  height: 36px;
  line-height: 36px;
  text-align: center;
  background-color: #444;
  color: #fff;
  font-weight: 400;
  font-size: 14px;
  border-radius: 3px;
}

</style>