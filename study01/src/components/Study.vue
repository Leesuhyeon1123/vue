<script setup>
import { ref } from "vue";
const message = ref("안녕! 나는 vue야");
const text = ref("💝💩💩");
const count = ref(0);
const minus = ref(0);
</script>
<template>
  <h1>{{ message }}</h1>
  <h2>{{ message }}</h2>
  <p>{{ message }}</p>
  <h3>{{ text }}</h3>
  <button @click="count++">➕수량 증가{{ count }}</button>
  <button @click="minus--">➖수량 감소{{ minus }}</button>
</template>
<style scoped>
h1 {
  color: pink;
}
h2 {
  color: blanchedalmond;
}
p {
  background-color: pink;
}
</style>
