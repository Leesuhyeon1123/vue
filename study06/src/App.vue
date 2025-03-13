<script setup>
import { ref } from "vue";
import ExArr from "./components/ExArr.vue";
import Event from "./components/Event.vue";
const eventbt = ref(false);
</script>

<template>
  <div>
    <ExArr />
    <div class="eventlist">
      <button @click="eventbt = !eventbt">
        {{ eventbt ? "닫기" : "vue Event 보기" }}
      </button>
      <Event v-if="eventbt" />
    </div>
  </div>
</template>

<style scoped>

</style>
