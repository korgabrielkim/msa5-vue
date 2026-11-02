<!-- 클릭 때마다 숫자가 올라가는 기능 만들기 -->
<script setup>
import { ref } from "vue";

// 데이터 바인딩을 먼저해야함.
// vue는 자동완성 기능을 적극적으로 활용. 힌트 우측편에 vue라고 나옴.
const count = ref(0); //ref와 reactive가 있는데, 현재는 그냥 ref만 사용하는 것이 권장되고 있음.
// 새로운 기능을 추가할 때에도 바인딩을 먼저 해줘야 함.
const bgColor = ref(""); // 빈문자열이 들어가 있는 것이 아니고 ref 객체가 들어가 있는 것임. 즉 ""은 빈문자열인 value임.
// const bgColor = ref(""); 접근하기 위해서 script 영역 안에서는 value를 지정해줘야 하고, template는 value를 지정해주지 않아도 됨.
const toggleBgColor = () => {
  if (bgColor.value === "") {
    bgColor.value = "bg-red";
  } else {
    bgColor.value = "";
  }
};
// ----- 양방향 데이터 바인딩 -----
// 양방향 데이터 바인딩 : (자바)스크립트에서 변경해도 템플릿(UI)과 연동 / 템플릿에서 변경해도 스크립트에 연동 되는 것.
// vue에서만 작동하는 기능임.
// 유저가 뭔가를 입력하는 경우에 많이 사용
const email = ref("");
</script>

<template>
  <!-- 어떤 요소든 이벤트를 줄 수 있음 / div에도 클릭 이벤트 가능. -->
  <!-- count의 약어는 보통 cnt를 사용함.  -->
  <!-- 연결할 때는 {{ 선언한 변수 }}하면 자동으로 디랜더링함. -->
  <!-- class 앞에서 @를 넣으면 vue에서 사용할 수 있는 기능들을 선택 가능하고 "명령을 작성해주면 됨." -->
  <div @click="count++" class="btn-cnt-up" :class="bgColor">
    Count is {{ count }}
    <!-- :클래스 ->디렉티브 속성이라고 함(반응을 주고 싶을 때 사용 / Vue의 동적 클래스 바인딩) -->
  </div>
  <button @click="count = 0">Count Reset</button>
  <button @click="count--" class="btn-cnt-down">Count Down</button>
  <button @click="bgColor = 'bg-red'">red</button>
  <button @click="bgColor = ''">pink</button>
  <button @click="toggleBgColor">toggle</button>
  <!-- 뷰의 경우에는 선언한 함수명에 즉시 실행함수를 넣어도 안넣어도 둘다 작동함 / 단, 파라미터를 주고 싶다면 ()을 꼭 넣어야함. -->
  <!-- 바닐라코드나 react 같은 경우에는 즉시 실행함수의 유무가 매우 중요함. -->
  <br /><br />
  <!-- <input type="text" name="email" id="email" :value="email" />{{ email }} -->
  <!-- ↑ 이렇게 작성하면, 단반향 데이터 바인딩이라고 볼 수 있음. -->
  <!-- {{ email }} : 자바스크립의 값을 출력하는 명령어 형식. -->
  <input type="text" name="email" id="email" v-model="email" />{{ email }}
  <!-- ↑ v-model이 양방향 데이터 바인등을 하는 코드임 -->
  <!-- v-model은 유저가 정보를 입력하는 곳에 주로 사용하고, value값을 자동으로 인식하지는 못함. -->
</template>

<style>
.btn-cnt-up {
  width: 100px;
  height: 100px;
  background-color: pink;
  text-align: center;
  margin: 0 auto;
  line-height: 100px;
  /* line-height는 %를 먹지 않음. */
}
.bg-red {
  background-color: red;
}
/* 코드 작성시 캐스케이딩(Cascading) 문제를 신경 써야함. */
/* 케스케이딩 : CSS에서 여러 스타일 규칙이 같은 요소에 적용될 때, 어떤 스타일을 최종적으로 적용할지 결정하는 과정 */
/* 만약, 동작을 넣었는데, 개발자 도구에서 오류 없이 정상적으로 작동하는데 변화가 없다면 캐스케이딩을 확인해 봐야함 */
</style>
