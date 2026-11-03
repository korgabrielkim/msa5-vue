<!-- props를 주로 사용하는 경우 -->
<!-- 부모에게 데이터가 있고(데이터를 가져 오는 것), 그 데이터를 자식들에게 전달해서 자식들이 읽기 전용으로 사용을 할 때. -->
<script setup>
import { ref } from "vue";
import Child from "./Child.vue";

const user = ref({
  id: 1,
  name: "홍길동",
  age: 20,
});
const str = ref("전달 문자열");
</script>
<template>
  <h2>Parent</h2>
  <!-- 자식에 데이타를 넘기는 방법 -->
  <!-- item(키)은 내가 임의로 정할 수 있지만, 다른 클래스명이나 겹치지 않게 작성하는 것이 좋음 -->
  <Child :item="user" :str="str"></Child>
</template>
<style></style>
