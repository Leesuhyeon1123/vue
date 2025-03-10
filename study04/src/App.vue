<script setup>
import Ifex from "./components/Ifex.vue";
import Vbind from "./components/Vbind.vue";
</script>

<template>
  <div class="wrap">
    <Ifex />
    <Vbind />
  </div>
</template>

<style scoped>
.wrap {
  display: flex;
}
.box {
  flex: 1;
  padding: 20px;
}
h2 {
  background-color: pink;
}
</style>
