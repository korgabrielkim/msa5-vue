<script setup>
import { ref } from "vue";

const btnActive = ref("profile");
</script>

<template>
  <main class="page">
    <section class="tab-card">
      <header class="card-header">
        <span class="eyebrow">MY SPACE</span>
        <h1>App Component</h1>
        <h2>TabUI</h2>
      </header>

      <div class="card-container" role="tablist" aria-label="페이지 메뉴">
        <button
          type="button"
          role="tab"
          :aria-selected="btnActive === 'profile'"
          :class="{ active: btnActive === 'profile' }"
          class="tab-button"
          @click="btnActive = 'profile'"
        >
          프로필
        </button>

        <button
          type="button"
          role="tab"
          :aria-selected="btnActive === 'setup'"
          :class="{ active: btnActive === 'setup' }"
          class="tab-button"
          @click="btnActive = 'setup'"
        >
          설정
        </button>

        <button
          type="button"
          role="tab"
          :aria-selected="btnActive === 'board'"
          :class="{ active: btnActive === 'board' }"
          class="tab-button"
          @click="btnActive = 'board'"
        >
          게시판
        </button>
      </div>

      <div class="card-content" role="tabpanel">
        <p v-if="btnActive === 'profile'">프로필 페이지 입니다.</p>
        <p v-else-if="btnActive === 'setup'">설정 페이지 입니다.</p>
        <p v-else>게시판 페이지 입니다.</p>
      </div>
    </section>
  </main>
</template>

<style>
* {
  box-sizing: border-box;
}

body {
  min-width: 320px;
  min-height: 100vh;
  margin: 0;
  background: #f4faff;
  color: #24354b;
  font-family: "Pretendard", "Noto Sans KR", sans-serif;
}

button {
  font: inherit;
}

.page {
  display: grid;
  min-height: 100vh;
  place-items: center;
  padding: 48px;
}

.tab-card {
  width: 560px;
  padding: 44px;
  border: 1px solid #e3effa;
  border-radius: 20px;
  background: #fff;
  box-shadow: 0 18px 50px rgb(64 134 196 / 10%);
}

.card-header {
  margin-bottom: 32px;
}

.eyebrow {
  display: inline-block;
  margin-bottom: 16px;
  color: #4596d8;
  font-size: 11px;
  font-weight: 700;
  letter-spacing: 0.16em;
}

.card-header h1 {
  margin: 0;
  color: #24354b;
  font-size: 30px;
  font-weight: 650;
  letter-spacing: -0.045em;
}

.card-header h2 {
  margin: 8px 0 0;
  color: #6d8ca8;
  font-size: 15px;
  font-weight: 500;
}

.card-container {
  display: flex;
  gap: 6px;
  padding: 6px;
  border: 1px solid #e7f1fa;
  border-radius: 12px;
  background: #f7fbff;
}

.tab-button {
  position: relative;
  flex: 1;
  padding: 13px 16px;
  border: 0;
  border-radius: 8px;
  background: transparent;
  color: #7890a6;
  cursor: pointer;
  font-size: 14px;
  font-weight: 500;
  transition:
    color 180ms ease,
    background-color 180ms ease;
}

.tab-button::after {
  position: absolute;
  right: 18px;
  bottom: 3px;
  left: 18px;
  height: 2px;
  border-radius: 2px;
  background: #48a8eb;
  content: "";
  transform: scaleX(0);
  transform-origin: center;
  transition: transform 180ms ease;
}

.tab-button:hover {
  background: #fff;
  color: #2788ce;
}

.tab-button:hover::after,
.tab-button.active::after {
  transform: scaleX(1);
}

.tab-button.active {
  background: #fff;
  color: #2788ce;
  font-weight: 650;
}

.tab-button:focus-visible {
  outline: 3px solid rgb(72 168 235 / 30%);
  outline-offset: 3px;
}

.card-content {
  display: grid;
  min-height: 170px;
  place-items: center;
  margin-top: 18px;
  padding: 28px;
  border: 1px solid #e8f2fa;
  border-radius: 12px;
  background: linear-gradient(135deg, #fff 20%, #f8fcff 100%);
}

.card-content p {
  margin: 0;
  color: #3c5872;
  font-size: 19px;
  font-weight: 500;
  letter-spacing: -0.025em;
}
</style>
