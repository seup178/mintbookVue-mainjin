<template>
  {{ state }}
    <div id="mypage_wrap">
      <div id="left_bar">
        <div id="profile_area">
          <div id="profile_img">
            <img
              src="../../assets/MyPage/mypage_userprofile.png"
              alt="mypage_profile"
            />
          </div>
        </div>
        <div id="menu_area">
          <ul>
            <li><a href="/mypage/mypage">구매내역</a></li>
            <li><a href="/mypage/mypick">찜</a></li>
            <li><a href="/mypage/cashpoint">캐시/포인트</a></li>
            <li><a href="/mypage/inquire">1:1 문의내역</a></li>
            <li><a href="/mypage/review/list">리뷰내역</a></li>
            <li><a href="/mypage/alimi" id="current">알리미</a></li>
            <li><a href="/mypage/myinfoedit">회원정보수정</a></li>
        </ul>
        </div>
      </div>
      <div id="right_content">
        <h4>구매내역상세</h4>
        <div>주문 상품 정보</div>
        <table class="table">
          <thead>
            <tr>
              <th scope="col">No.</th>
              <th scope="col">상품명</th>
              <th scope="col">수량</th>
              <th scope="col">가격</th>
            </tr>
          </thead>
          <tbody>
            <tr >
              <td>1</td>
              <td>
                <span>방주</span><br>
                <span style="color: #919191;">유키 하루오지음,김은모</span>
              </td>
              <td>1</td>
              <td>14,500원</td>
            </tr>
          </tbody>
        </table>
        
        <div>기본/배송정보</div>
        <table class="table">
          <tbody>
                <tr>
                    <th scope="row">주문자명</th>
                    <td>홍길동</td>
                    <th scope="row">수령자명</th>
                    <td>김철수</td>
                </tr>
                <tr>
                    <th scope="row">배송지</th>
                    <td colspan="3">부산광역시 부산진구 중앙대로 668 (A1프라자6층)</td>
                </tr>
                <tr>
                    <th scope="row">전화번호</th>
                    <td>010-1234-1234</td>
                    <th scope="row">휴대번호</th>
                    <td>010-1234-1234</td>
                </tr>
                <tr>
                    <th scope="row">주문번호</th>
                    <td>001-1295-10123-A1234956</td>
                    <th scope="row">배송방법</th>
                    <td>택배</td>
                </tr>
                <tr>
                    <th scope="row">주문접수일</th>
                    <td colspan="3">2023년 03월 31일 금 11시 44분</td>
                </tr>
                <tr>
                    <th scope="row" style="height: 100px;">상태</th>
                    <td colspan="3">출고완료/집하(2023-03-31)<br><button>배송중</button></td>
                </tr>
                <tr>
                    <th scope="row">수령예상일</th>
                    <td colspan="3">2023년 04월 01일 금 21시</td>
                </tr>
            </tbody>
        </table>
        <div>결제 정보</div>
        <table class="table">
            <tbody>
                <tr>
                    <th scope="row">총주문 금액</th>
                    <td colspan="3">34,000원(상품가격 34,000원 + 배송료 0원)</td>
                </tr>
                <tr>
                    <th scope="row">실 결제금액</th>
                    <td colspan="3"><span style="color: #3DDCA3;">19,600원</span>(포인트사용: 1,000원)</td>
                </tr>
                <tr>
                    <th scope="row">결제방법</th>
                    <td colspan="3">신용카드</td>
                </tr>
            </tbody>
        </table>


      </div>
    </div>
  </template>
  
  <script>
import { reactive } from 'vue';
import { useRoute } from 'vue-router';
import axios from 'axios';
  export default {
    setup() {
      const route = useRoute();

      const state = reactive({
        no: Number(route.query.no),
        id: Number(route.query.id),
        order:""
      });

      const load=() =>{
        axios.get(`/api/mypage/read/detail?no=${state.no}&id=${state.id}`).then((res)=>{
          console.log(res.data);
          state.order = res.data;
        })
      };
      load();



      return {state};
    },
  };
  </script>
  
  <style lang="css" scoped>
  a {
    text-decoration: none;
    color: inherit;
  }
  
  #mypage_wrap {
    margin: 0 auto;
    width: 1200px;
    overflow: hidden;
    margin-top: 60px;
    display: flex;
  }
  #left_bar {
    width: 200px;
  }
  #profile_area {
    width: 176px;
    height: 146px;
    background-color: #3ddca3;
    border-radius: 15px;
    position: relative;
  }
  #profile_img {
    width: 70px;
    height: 70px;
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
  }
  #menu_area {
    width: 176px;
    height: 281px;
    border-radius: 20px;
    border: 3px solid #3ddca3;
    margin-top: 20px;
  }
  #menu_area > ul {
    width: 150px;
    margin-top: 20px;
  }
  #menu_area > ul > li {
    padding: 4px 0;
    font-size: 17px;
  }
  #right_content {
    width: 1000px;
    
  }
  #current {
    font-weight: bold;
  }
  .table{
          width: 100%;
          margin-top:30px;
          margin-bottom: 30px;
      }
  
      .table{
        width: 100%;
        margin-top:30px;
    }

  </style>
  