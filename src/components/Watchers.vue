<script setup>
import { ref, watch } from "vue";
const test = ref("");
const testErrorMsg = ref("");
const testColor = ref("");
// 변수 선언한 객체(test)를 스테이트라고 부름.
// Watchers
watch(test, (val) => {
  // 유효성 검사와 비슷한 기능 구현(정규 표현식)
  // 입력하면 import { ref, watch } from "vue"; ← 여기에 watch가 자동으로 추가됨.
  // watch(내가 감시하고 싶은 스테이트, 내가 실행시키고 싶은 처리를 콜백함수로 작성)
  const pattern = /^[a-zA-Z]+$/;
  // ※ new 객체를 인스텐스화 하기 위한 코드.
  if (val === "") {
    testErrorMsg.value = "";
  } else if (pattern.test(val)) {
    testErrorMsg.value = "O";
    testColor.value = "color:green;";
  } else {
    testErrorMsg.value = "X";
    testColor.value = "color:red;";
  }
});
</script>
<template>
  <h2>Watchers : 감시자</h2>

  <input type="text" v-model="test" />
  <!-- {{ test }} -->
  <!-- watchers는 <input type="text" v-model="test" />의 input의 값이 아니라 스테이트의 값을 추적하는 것임. -->
  <!-- watchers는 양방향 데이터 바인딩이 가능해야 작동함 / So, 리엑트에서는 작동 X -->
  <p :style="testColor">{{ testErrorMsg }}</p>
</template>
<style></style>
