<!-- 클릭 때마다 숫자가 올라가는 기능 만들기 -->
<script setup>
import { ref } from "vue";

// 데이터 바인딩을 먼저해야함.
// vue는 자동완성 기능을 적극적으로 활용. 힌트 우측편에 vue라고 나옴.
const count = ref(0);
</script>

<template>
  <!-- 어떤 요소든 이벤트를 줄 수 있음 / div에도 클릭 이벤트 가능. -->
  <!-- count의 약어는 보통 cnt를 사용함.  -->
  <!-- 연결할 때는 {{ 선언한 변수 }}하면 자동으로 디랜더링함. -->
  <!-- class 앞에서 @를 넣으면 vue에서 사용할 수 있는 기능들을 선택 가능하고 "명령을 작성해주면 됨." -->
  <div @click="count++" class="btn-cnt">Count is {{ count }}</div>
  <button @click="count = 0">Count Reset</button>
</template>

<style>
.btn-cnt {
  width: 100px;
  height: 100px;
  background-color: pink;
  text-align: center;
  margin: 0 auto;
  line-height: 100px;
  /* line-height는 %를 먹지 않음. */
}
</style>
