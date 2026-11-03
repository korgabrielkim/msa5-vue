<script setup>
import { ref } from "vue";
import axios from "axios";

// 1. 반응형 데이터
const photos = ref([]);
const page = ref(1);
const limit = 3;
const loading = ref(false);

// 2. 다음 버튼 클릭 시 실행할 함수
const getPhotos = async () => {
  // 중복 클릭 방지
  if (loading.value) return;

  loading.value = true;

  const baseUrl = "https://picsum.photos";
  const path = "/v2/list";
  const url = `${baseUrl}${path}?page=${page.value}&limit=${limit}`;

  try {
    // API 데이터 요청
    const response = await axios.get(url);

    // 기존 데이터에 새 데이터 추가
    photos.value.push(...response.data);

    // 요청 성공 후 페이지 번호 증가
    page.value += 1;
  } catch (error) {
    console.error("데이터 요청 실패:", error);
  } finally {
    // 요청 완료 후 버튼 활성화
    loading.value = false;
  }
};

// 3. 초기화 버튼 클릭 시 실행할 함수
const resetPhotos = () => {
  photos.value = [];
  page.value = 1;
};
</script>

<template>
  <div class="container">
    <div class="title">
      <h1>사진 3장씩 추가(❁´◡`❁)</h1>

      <div class="btn">
        <button class="next-btn" @click="getPhotos" :disabled="loading">
          {{ loading ? "Loading..." : "Add" }}
        </button>

        <button class="reset-btn" @click="resetPhotos">Reset</button>
      </div>
    </div>

    <div class="card-container">
      <div class="card" v-for="item in photos" :key="item.id">
        <div
          class="card-img"
          :style="{ backgroundImage: `url(${item.download_url})` }"
        ></div>

        <div class="card-txt">{{ item.id }} : {{ item.author }}</div>
      </div>
    </div>
  </div>
</template>

<style scoped>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

.container {
  width: 90%;
  max-width: 1200px;
  margin: 50px auto;
}

/* 제목 영역 */
.title {
  padding: 10px 0;
  margin-bottom: 25px;
}

.title h1 {
  font-size: 38px;
  font-weight: 700;
  color: #222;
  letter-spacing: -1.5px;
}

/* 버튼 영역 */
.btn {
  display: flex;
  gap: 10px;
  margin-top: 18px;
}

.btn button {
  padding: 11px 25px;
  border: none;
  border-radius: 7px;
  font-size: 14px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.25s ease;
}

/* Add 버튼 */
.next-btn {
  background-color: #263b59;
  color: #fff;
}

.next-btn:hover:not(:disabled) {
  background-color: #3c587c;
  transform: translateY(-2px);
  box-shadow: 0 5px 12px rgba(38, 59, 89, 0.2);
}

/* Reset 버튼 */
.reset-btn {
  background-color: #f0f1f3;
  color: #444;
}

.reset-btn:hover {
  background-color: #dfe3e8;
  transform: translateY(-2px);
}

/* 비활성화 */
.next-btn:disabled {
  opacity: 0.5;
  cursor: not-allowed;
}

/* 이미지 카드 영역 */
.card-container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 28px 22px;
}

/* 이미지 */
.card-img {
  width: 100%;
  aspect-ratio: 1 / 1;
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  border-radius: 9px;
  overflow: hidden;
}

/* 이미지 설명 */
.card-txt {
  padding: 10px 5px;
  color: #555;
  font-size: 15px;
  text-align: left;
}

/* 모바일 대응 */
@media (max-width: 600px) {
  .title h1 {
    font-size: 28px;
  }

  .card-container {
    grid-template-columns: repeat(2, minmax(0, 1fr));
    gap: 18px 12px;
  }
}
</style>
