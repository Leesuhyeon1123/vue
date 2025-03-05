<script setup>
import { ref, computed } from "vue";
// serch = ref("") 사용자가 입력한 검색어를 저장하는 변수
const serch = ref("");
const items = ["아이폰", "갤럭시", "맥북"];
// filteredItems(computed) : 사용자가 입력한 검색어
// (serch.value)가 포함된 includes() 상품만 보여줌
const filteredItems = computed(() => {
  return items.filter((item) => item.includes(serch.value));
});
// -------------------------------------------
// 상품 리스트 표시
const products = ["사과🍎","딸기🍓","복숭아🍑"]
const materials = ["화장품🧴","여벌옷👕","선글라스🕶"]
</script>
<template>
    <h2>검색 기능🔍</h2>
  <!-- 사용자가 입력한 검색어를 search 변수에 자동으로 반영 -->
  <input v-model="serch" placeholder="상품 검색" />
  <ul>
    <!-- v-for 반복문 사용해서 filteredItems 배열을 돌면서 li태그로 상품 표시 -->
    <li v-for="item in filteredItems" :key="item">{{ item }}</li>
  </ul>
  <hr>
<!-- --------------------------------------------------------- -->
  <h2>상품 리스트 출력🛒</h2>
  <ul>
  <li v-for="product in products" :key="product">{{ product }}</li>
  </ul>
  <hr>
  <!-- --------------------------------------------------------- -->
  <h2>여행 준비물 리스트 출력🎒</h2>
  <ul>
  <li v-for="material in materials" :key="material">{{ material }}</li>
  </ul>
</template>
<style scoped></style>
