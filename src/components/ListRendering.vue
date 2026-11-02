<!-- 조건부 랜더링 -->
<script setup>
import { ref } from "vue";
const items = ref([
  {
    id: 1,
    kinds: "중식",
    food: "짜장면",
  },
  {
    id: 2,
    kinds: "한식",
    food: "비빔밥",
  },
  {
    id: 3,
    kinds: "일식",
    food: "돈까스",
  },
]);
</script>

<template>
  <h2>List ListRendering</h2>
  <div class="container">
    <div v-for="item in items" :key="item.id" class="card">
      <!-- <div v-for="변수 in 루트를 돌리고 싶은 원문" :key="고유값ex)id" class="card"> 원문이 items와 같이 복수명이면 변수로는 단수형을 관례상 많이 사용함. -->
      <p>{{ item.kinds }}</p>
      <p>{{ item.food }}</p>
    </div>
  </div>
</template>

<style></style>
