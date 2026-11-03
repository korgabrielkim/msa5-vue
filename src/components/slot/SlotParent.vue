<script setup>
import SlotChild from "./SlotChild.vue";
</script>
<template>
  <h2>Slot Parent</h2>
  <SlotChild>부모에서 보낸 컨텐츠 정보</SlotChild>
  <SlotChild>전송</SlotChild>
  <SlotChild></SlotChild>
</template>
<style scoped>
/* 해당 컴포넌트에만 영향이 가도록 설정하는 방법임.(스타일 전파 현상을 막을 수 있음) */
/* 주의할 점 */
/* scopred로 하더라도 자식 컴포넌트 요소 중 최상위 요소는 부모의 영향을 받음. */
/* 그래서 자식에서 템프릿을 형성할 때 최상위 div를 만들고 작성하는 것이 좋음. */
</style>
