<script setup>
import { ref } from "vue";
const btnActive = ref("profile");
</script>

<template>
  <h1>App Component</h1>
  <h3>TabUI</h3>
  <div class="card-container">
    <button
      :class="{ active: btnActive === 'profile' }"
      class="btn-profile btn"
      @click="btnActive = 'profile'"
    >
      프로필
    </button>
    <button
      :class="{ active: btnActive === 'setup' }"
      class="btn-setup btn"
      @click="btnActive = 'setup'"
    >
      설정
    </button>
    <button
      :class="{ active: btnActive === 'board' }"
      class="btn-board btn"
      @click="btnActive = 'board'"
    >
      게시판
    </button>
  </div>
  <div class="card-content">
    <p v-if="btnActive === 'profile'">프로필 페이지 입니다.</p>
    <p v-else-if="btnActive === 'setup'">설정 페이지 입니다.</p>
    <p v-else>게시판 페이지 입니다.</p>
    <!-- TapUI -->
    <!-- 데이터를 받아 와야 하기 때문에 v-show 보다는 v-if 문이 조금더 적합함.  -->
    <!-- 왜냐하면 v-show 경우에는 처음 로딩이 될 때 모든 페이지 소스를 받아 오기 때문에. -->
    <!-- <p v-show="btnActive === 'profile'">프로필 페이지 입니다.</p> -->
    <!-- <p v-show="btnActive === 'setup'">설정 페이지 입니다.</p> -->
    <!-- <p v-show="btnActive === 'board'">게시판 페이지 입니다.</p> -->
  </div>
</template>

<style>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
ul,
li {
  list-style: none;
}
p {
  font-family: "Hahmlet", serif;
  font-optical-sizing: auto;
  font-weight: 400;
  font-style: normal;
  padding: 30px;
  font-size: 30px;
}
a {
  color: #333;
}
.card-container {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
}
.btn {
  width: 100px;
  /* height: 50px; */
  cursor: pointer;
  font-size: 18px;
  background-color: #d66b91;
  border-radius: 10px;
  color: white;
  font-family: "Hahmlet", serif;
  font-optical-sizing: auto;
  font-weight: 400;
  font-style: normal;
  padding: 10px;
  border: none;
  box-shadow: 1px 1px 5px #333;
}

.btn:hover {
  color: #6478e8;
  font-weight: 500;
}
.active {
  border-bottom: 2px solid #6478e8;
  color: #6478e8;
  background-color: aliceblue;
}
</style>
