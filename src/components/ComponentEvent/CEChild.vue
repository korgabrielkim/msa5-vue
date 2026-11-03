<script setup>
import { ref } from "vue";
</script>
<template>
  <h2>CEChild</h2>
  <button @click="$emit('addCount')">add</button>
  <!-- <button @click="$emit← 글로벌 함수">add</button> -->
  <button @click="$emit('multiCount', 2)">곱하기</button>
  <!-- <button @click="$emit('multiCount', 전달할 파라멘트를 적으면 됨)"></button> -->
</template>
<style></style>
