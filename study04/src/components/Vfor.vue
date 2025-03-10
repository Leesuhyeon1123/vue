<script setup>
import { ref } from "vue";
import Vforlist from "./Vforlist.vue";
const products = ref(["노트북", "스마트폰", "태블릿"]);
const fruits = ref(["사과", "바나나", "포도"]);
const showfor = ref(false);
</script>
<template>
  <div>
    <h2>V-for</h2>
    <!-- v-for -->
    <div>
      <ul>
        <li v-for="(product, index) in products" :key="product">
          💚 {{ index + 1 }}. {{ product }}
        </li>
      </ul>
      <br />
      <strong v-for="fruit in fruits" :key="fruit"> 💜 {{ fruit }}</strong>
    </div>
    <hr />
    <!-- V-for-list 예제 -->
    <div class="for-list">
      <h3>for-list 예제</h3>
      <button @click="showfor = !showfor">
        {{ showfor ? "닫아" : "보여조" }}
      </button>
      <!-- for-list -->
      <Vforlist v-if="showfor" />
    </div>
  </div>
</template>
<style scoped>
h2 {
  background-color: pink;
}
li {
  list-style: none;
}
div {
  padding: 20px 0;
}
</style>
