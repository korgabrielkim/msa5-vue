<script setup>
import CEChild from "./CEChild.vue";
import { ref } from "vue";
const count = ref(0);
// 부모가 자식에게 권한을 줄 함수를 선언을 선행적으로 해야함.
const addCount = () => {
  count.value++;
};
const multiCount = (val) => {
  // count.value = count.value * val;
  count.value /= val;
};
</script>
<template>
  <h2>CEParent</h2>
  <CEChild @addCount="addCount" @multiCount="multiCount"></CEChild>
  <!-- <CEChild @해당 이름으로="여기 함수를" 자식에게 보내겠다는 의미></CEChild> -->

  <p>카운트 : {{ count }}</p>
  <button @click="count++">add</button>
</template>
<style></style>
