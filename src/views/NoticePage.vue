<template>
  <div class="total_wrap">
    <div class="center_wrap">
      <div class="headerpage"></div>
      <div id="divide_section">
        <div id="category">
          <p id="category_title">고객센터</p>
          <ul>
            <li><a href="/cs/register">1:1문의접수</a></li>
            <li><a href="/faq">자주 묻는 질문</a></li>
            <li><a href="/notice" id="bold">공지사항</a></li>
          </ul>
        </div>
        <div id="section">
          <p id="maintitle">공지사항</p>
          <table class="table">
            <thead>
              <tr>
                <th scope="col" id="th_no">No.</th>
                <th scope="col" id="th_title">제목</th>
                <th scope="col" id="th_date">등록일</th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <th scope="row" class="td_no">1</th>
                <td class="td_title">배송비 정책 변경 안내(2/20~)</td>
                <td class="td_date">2023.02.12</td>
              </tr>
              <tr>
                <th scope="row" class="td_no">2</th>
                <td class="td_title">배송비 정책 변경 안내(2/20~)</td>
                <td class="td_date">2023.02.12</td>
              </tr>
              <tr>
                <th scope="row" class="td_no">3</th>
                <td class="td_title">배송비 정책 변경 안내(2/20~)</td>
                <td class="td_date">2023.02.12</td>
              </tr>
              <tr>
                <th scope="row" class="td_no">4</th>
                <td class="td_title">배송비 정책 변경 안내(2/20~)</td>
                <td class="td_date">2023.02.12</td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
      <div>
        <el-backtop :right="70" :bottom="70" style="color: #3ddca3" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  setup() {
    return {};
  },
};
</script>

<style lang="css" scoped>
/* 초기화 */
* {
  padding: 0;
  margin: 0;
}

ul,
li {
  list-style: none;
}

a {
  text-decoration: none;
  color: black;
}

/*1200px 중앙정렬 */
.center_wrap {
  width: 1200px;
  margin: 0 auto;
}

/*HeaderPage용 공백 */
.headerpage {
  height: 95px;
}

/*페이지 타이틀 영역 */
.maintitle_wrap {
  height: 30px;
  padding-bottom: 50px;
}
.maintitle_wrap > li {
  float: left;
}

.maintitle_wrap > li > img {
  width: 35px;
  margin-right: 10px;
}

#maintitle {
  font-size: 24px;
  font-weight: bold;
  margin-bottom: 50px;
  margin-top: 50px;
}

/*사이드 카테고리 영역*/
#divide_section {
  display: grid;
  grid-template-columns: 247px auto;
}

#category {
  padding-top: 50px;
}

#category_title {
  font-size: 18px;
  font-weight: bold;
  margin-bottom: 25px;
}

#category > ul > li {
  font-size: 15px;
  margin-bottom: 10px;
}

#category > ul > li > a:hover {
  font-weight: bold;
  color: black;
}

#bold {
  font-weight: bold;
}

/*테이블 영역 */
table {
  font-size: 14px;
  margin-bottom: 50px;
}

thead {
  text-align: center;
  border-top: 1px solid gray;
}

#th_no {
  width: 100px;
}

#th_date {
  width: 150px;
}

.td_no {
  text-align: center;
}

.td_title {
  padding-left: 20px;
  cursor: pointer;
}

.td_date {
  text-align: center;
}

tbody > tr > th,
tbody > tr > td {
  padding-top: 20px;
  padding-bottom: 20px;
}
</style>
