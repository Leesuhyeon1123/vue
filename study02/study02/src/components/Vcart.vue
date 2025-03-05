<script setup>
import { ref } from "vue";
const products = ["사과🍎", "딸기🍓", "복숭아🍑"];
const cart = ref([]);
const addTocart = (product) => {
  cart.value.push(product);
};
</script>
<template>
  <h2>상품 목록🛍</h2>
  <ul>
    <li v-for="product in products" :key="product">{{ product }} <button @click="addTocart(product)">추가</button></li>
  </ul>
  <h2>장바구니🛒</h2>
  <ul>
    <li v-for="item in cart" :key="item">{{ item }}</li>
  </ul>
</template>
<style scoped></style>
