<script setup>
// import → 변수 선언 → 함수 작성 → 라이프스타일 훅스는 그 밑에 작성하는 것이 좋음.
import axios from "axios"; // 확장자가 없을 때에는 노드 모듈스에 들어가 있는 상태라고 보면 됨. / 내가 만들 설정을 불러 올때는 꼭 확장자를 넣어줘야 함.
import { onBeforeMount, ref } from "vue";
const cards = ref([]);
// 마운트 되기전 데이터를 받아와야함. 그래야 리소스를 덜 사용함.
const page = ref(1); // page는 1이 담긴 것이 아니라 ref(value)이 담겨져 있는 것임 / 그래서 자바에서는 Let 사용했지만, Vue에서는 const를 사용함.
const limit = 3;
// 대입 연산자는 = 을 기준으로 우측을 먼저 실행함 → 그리고 그 결과값을 좌측에 있는 변수에 저장함.

const getNextPage = async () => {
  try {
    const url = "https://picsum.photos/v2/list";
    const config = {
      params: {
        page: page.value,
        limit: limit,
      },
    };
    const response = await axios.get(url, config);
    cards.value.push(...response.data);
    // push 자체가 파라미터를 여러개 받을 수 있음 / ...은 동적 파라미터 : 몇개가 될지 모르겠지만 니가 보내주는거 다 받을거라는 의미
    page.value++;
  } catch (error) {
    console.error(error);
  }
};
const resetBtn = () => {
  cards.value = [];
  page.value = 1;
};
const firstReset = () => {
  cards.value = cards.value.slice(0, limit);
  page.value = 2; // 잘린 후 이제는 여기서 부터 시작하라는 의미임.
};
onBeforeMount(getNextPage);
</script>

<template>
  <div class="card-container">
    <!-- card를 루트 돌린다고 생각하면 됨 -->
    <div v-for="item in cards" :key="item.id" class="card">
      <div
        class="card-img"
        :style="{ backgroundImage: `url(${item.download_url})` }"
      ></div>
      <div class="card-text">{{ item.id }}: {{ item.author }}</div>
      <!-- <div class="card-text">{{ `${item.id}: ${item.author} ` }}</div> -->
    </div>
  </div>
  <button @click="getNextPage">Add Page</button>
  <button @click="resetBtn">Reset</button>
  <button @click="firstReset">First Page</button>
</template>

<style scoped>
.card-container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(205px, 1fr));
  gap: 10px;
}
.card {
  display: flex;
  flex-direction: column;
  gap: 10px;
}
.card-img {
  aspect-ratio: 4/3;
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
}
</style>
