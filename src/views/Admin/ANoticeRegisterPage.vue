<template>
  <div id="total_wrap">
    <div id="divide_wrap">
      <div id="nav_wrap">
        <admin-menu-page></admin-menu-page>
      </div>
      <div id="content_wrap">
        <p id="maintitle">공지사항 등록</p>
        <table class="table">
          <tbody>
            <tr>
              <th scope="row">제목</th>
              <td colspan="3">
                <input
                  type="text"
                  v-model="state.title"
                  placeholder="제목을 입력하세요."
                />
              </td>
            </tr>
            <tr>
              <th scope="row">내용</th>
              <td colspan="3">
                <textarea
                  cols="30"
                  rows="10"
                  placeholder="내용을 입력하세요."
                  v-model="state.content"
                ></textarea>
              </td>
            </tr>
          </tbody>
        </table>
        <div id="register_wrap">
          <button @click="noticeWrite()">등록</button>
          <router-link to="/admin/notice"><button>취소</button></router-link>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { reactive } from "vue";
import AdminMenuPage from "../../components/AdminMenuPage.vue";
import axios from "axios";
import { useRouter } from "vue-router";

export default {
  components: {
    AdminMenuPage,
  },

  setup() {
    const router = useRouter();

    const state = reactive({
      title: "",
      content: "",
    });

    //공지사항 등록
    const noticeWrite = async () => {
      const url = `/api/notice/write`;
      const headers = { "Content-Type": "application/json" };
      const body = new FormData();
      body.append("title", state.title);
      body.append("content", state.content);
      await axios
        .post(url, body, { headers })
        .then(() => {
          alert("공지사항을 등록하였습니다.");
          router.push({ path: "/admin/notice" });
        })
        .catch((err) => {
          console.log(err);
          alert("공지사항 등록에 실패했습니다.");
        });
    };

    return {
      state,
      noticeWrite,
    };
  },
};
</script>

<style lang="css" scoped>
/*초기화 */
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
a:hover {
  color: black;
  font-weight: bold;
}

/*전체 페이지 영역 */
#divide_wrap {
  /* width: 1920px; */
  display: grid;
  grid-template-columns: 290px auto;
}

#content_wrap {
  padding-left: 30px;
  padding-right: 30px;
}

/*사이드메뉴 영역 */
#nav_wrap {
  background: rgb(223, 223, 223);
  height: 100vh;
}

/*콘텐츠 상단 영역 */
#maintitle {
  font-size: 24px;
  font-weight: bold;
  margin-top: 50px;
  margin-bottom: 50px;
}

button {
  width: 100px;
  border-radius: 5px;
  color: white;
  background: black;
  margin-bottom: 30px;
  margin-left: 10px;
}

#edit {
  margin-left: 50px;
  float: right;
}

/*콘텐츠 하단 영역 */

.table {
  width: 100%;
  margin-top: 30px;
}

th {
  width: 200px;
  background: rgb(184, 184, 184);
}

#register_wrap {
  display: flex;
  justify-content: center;
}

input[type="text"] {
  width: 80%;
  border-radius: 5px;
  border: 0.5px solid rgb(184, 184, 184);
  padding-left: 10px;
}
textarea {
  width: 80%;
  border-radius: 5px;
  border: 0.5px solid rgb(184, 184, 184);
  padding-left: 10px;
}
</style>
