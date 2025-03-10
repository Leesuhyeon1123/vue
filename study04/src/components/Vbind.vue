<script setup>
import Vfor from "./Vfor.vue";
import { ref } from "vue";
const imgurl = ref("https://vuejs.org/images/logo.png");
const link = ref("https://naver.com");
const count = ref(0);
const increase = () => {
  count.value++;
};
const decrease = () => {
  count.value--;
};
const txt = ref("");
const items = ref(["💛", "💙", "💜"]);
</script>
<template>
  <div class="box">
    <h2>V-bind</h2>
    <hr />
    <!-- 속성 바인딩 -->
    <div>
      <img :src="imgurl" alt="메롱" />
      <a :href="link" target="_blank"> 네이버 이동 </a>
    </div>
    <hr />
    <!-- 이벤트 바인딩 -->
    <div>
      <button @click="decrease">-</button>
      <span>{{ count }}</span>
      <button @click="increase">+</button>
    </div>
    <hr />
    <!-- 양방향 바인딩 -->
    <div>
      <input v-model="txt" />
      <p>메모: {{ txt }}</p>
    </div>
    <hr />
    <!-- 반복 렌더링 v-for -->
    <div>
      <ul>
        <li v-for="(item, index) in items" :key="item">
          {{ index + 1 }}. {{ item }}
        </li>
      </ul>
    </div>
    <hr />
  <Vfor />
  </div>
</template>
<style scoped>
h2 {
  background-color: pink;
}
img {
  width: 50px;
  height: 50px;
}
span {
  margin: 0 10px;
}
div {
  padding: 20px 0;
}
li {
  list-style: none;
}
</style>
