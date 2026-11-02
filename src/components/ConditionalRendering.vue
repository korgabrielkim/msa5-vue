<!-- 조건부 랜더링 -->
<script setup>
import { ref } from "vue";
const num = ref(0);
const flg = ref(true);
</script>

<template>
  <input type="number" v-model="num" />
  <p v-if="num === 0">0</p>
  <!-- ↑ javaScript의 if문이라고 볼 수 있음 -->
  <p v-else-if="num % 2 === 0">짝수 입니다.</p>
  <p v-else>홀수 입니다.</p>
  <hr />
  <hr />
  <!-- v-show -->

  <!-- <button :class="{ '추가할 클래스명': 조건, '추가할 클래스명': 조건 → ,를 이용해서 추가 가능함.(객체이기 때문에) }" @click="flg = !flg"> -->
  <button :class="{ 'btn-toggle': flg === false }" @click="flg = !flg">
    토글
  </button>
  <!-- ↑ true = false(!가 flg의 부정이라는 의미임.)로 바뀌는 것임 / 처음에는 뒷쪽에 있는 대입 연산자가 먼저 작동됨. -->
  <p v-if="flg">v-if</p>
  <!-- ↑ 요소를 만들었다가 지웠다가를 반복함 / 조건이 여러 개일 때 적합 -->
  <p v-show="flg">v-show</p>
  <!-- ↑ dom 자체를 배정 / 빠르기에 자주 반복하는 상황에 적합 / 스타일만 변한다고 볼 수 있음 / 랜더링 비용이 적게 소요됨. -->
</template>

<style>
.btn-toggle {
  background-color: rgb(8, 124, 124);
}
</style>
