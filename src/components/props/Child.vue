<script setup>
// 부모 요소를 불러 오는 함수
import { defineProps } from "vue"; // defineProps의 경우, 더이상 import 할 필요가 없음 // 자주 사용하는 핵심 기능이라고 함.
const props = defineProps({
  // 받을 때 객체로 받음
  item: Object,
  str: String,
});
</script>
<template>
  <h2>Child</h2>
  <p>{{ props.item.name }}</p>
  <!-- 부모에게 받아온 데이터는 기본적으로 읽기 전용 / 자식쪽에서 수정 X -->
</template>
<style></style>
