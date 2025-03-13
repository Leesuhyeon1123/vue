<script setup>
import { ref } from "vue";

const items = ref(["Apple🍎", "Banana🍌", "Cherry🍒", "Orange🍊", "Grapes🍇"]);
// push()-추가
const addItem = () => {
  items.value.push("Pineapple🍍"); // 배열에서 추가
};
const removeLastItem = () => {
  items.value.pop(); // 배열의 마지막 제거
};
const removeFirstItem = () => {
  items.value.shift();
};
const addFirstItem = () => {
  items.value.unshift("mango🥭");
};
const removeAndAddItem = () => {
  // splice(인덱스번호, delete갯수, 추가내용아이템)
  items.value.splice(1, 1, "kiwi🥝");
};
const sortItems = () => {
  items.value.sort();
};
// reverse() - 역순 정렬
const reverseItems = () => {
  items.value.reverse();
};
const filterItems = () => {
  items.value = items.value.filter((item) => item.includes("a"));
};
const concatItems = () => {
  items.value = items.value.concat(["strawberry🍓", "melon🍈"]);
};
const sliceItems = () => {
  // (시작 넘버, 마지막 넘버)
  items.value = items.value.slice(1, 3);
};
</script>
<template>
  <div>
    <h2>배열 조작 예제(배열 종류)</h2>
    <p>현재 배열 : {{ items }}</p>
    <div class="btn-wrap">
      <!-- push() :버튼 클릭했을때 배열에 추가되게함 -->
      <button @click="addItem">push()-추가</button>
      <!-- pop() : 마지막 제거 -->
      <button @click="removeLastItem">pop() - 마지막 제거</button>
      <!-- shift() : 첫번째 제거 -->
      <button @click="removeFirstItem">shift() - 첫 번째 제거</button>
      <!-- unshift() : 첫번째 추가 -->
      <button @click="addFirstItem">unshift() - 첫 번째 추가</button>
      <!-- splice() : 요소 변경 -->
      <button @click="removeAndAddItem">splice() - 요소 변경</button>
      <!-- sort() : 정렬 -->
      <button @click="sortItems">sort() - 정렬</button>
      <!-- reverse() : 역순정렬 -->
      <button @click="reverseItems">reverse() - 역순 정렬</button>
      <!-- filter() : 'a'포함된 요소만 정렬-->
      <button @click="filterItems">filter() - 'a' 포함된 요소만</button>
      <!-- concat() : 새로운 배열과 결합 -->
      <button @click="concatItems">concat() - 새로운 배열과 결합</button>
      <!-- slice() : 인덱스 1~2 요소 추출 -->
      <button @click="sliceItems">slice() - 인덱스 1~2 요소 추출</button>
    </div>
  </div>
</template>
<style scoped>
button {
  margin: 5px;
  padding: 10px;
  border: none;
  background: rgb(238, 255, 190);
  color: rgb(0, 0, 0);
  cursor: pointer;
}
button:hover {
  background: rgb(223, 255, 201);
}
.btn-wrap {
  margin-top: 30px;
}
</style>
