<script setup>
import { computed, reactive, ref } from "vue";
// ref로 count 상태 관리
const count = ref(0);
const increase = () => {
  count.value++;
};
// reative로 user 객체 관리
const user = reactive({
  name: "수현",
});
const toggleName = () => {
  // 삼항 연산자 조건
  user.name = user.name === "수현" ? "삐모" : "수현";
};
// computed로 count 값을 두배로 계산
const doubleCount = computed(() => count.value * 2);
// computed 계산된 값 만들기
const price = ref(100);
const quantity = ref(2);
const totalPrice = computed(() => price.value * quantity.value);
// ex01
const ex01Price = ref(500);
const ex01quantity = ref(2);
const ex01totalPrice = computed(() => ex01Price.value * ex01quantity.value);
</script>

<template>
  <div>
    <!-- ref로 count 상태 관리 -->
    <p>Count : {{ count }}</p>
    <button @click="increase">+증가</button>

    <!-- reactive로 user 객체 관리 -->
    <p>User Name : {{ user.name }}</p>
    <button @click="toggleName">Toggle Name</button>

    <!-- computed로 count 값을 두배로 계산 -->
    <button>Double Count : {{ doubleCount }}</button>
    <hr />
    <!-- computed 계산된 값 만들기 -->
    <h3>computed로 계산</h3>
    <div class="computed">
      <div class="ex01">
        <p>가격: {{ price }}원</p>
        <p>수량: {{ quantity }}개</p>
        <p>총 가격: {{ totalPrice }}원</p>
      </div>
      <div class="ex02">
        <p>가격: {{ ex01Price }}원</p>
        <button @click="ex01Price += 10">가격 +10원</button>
        <button @click="ex01Price -= 10">가격 -10원</button>
        <hr />
        <p>수량: {{ ex01quantity }}개</p>
        <button @click="ex01quantity += 1">수량 +1</button>
        <!-- disabled = 1밑으로 숫자 안떨어지게 비활성화시키기 -->
        <button @click="ex01quantity -= 1" :disabled="ex01quantity <= 1">수량 -1</button>
        <p>총 가격: {{ ex01totalPrice }}원</p>
      </div>
    </div>
  </div>
</template>

<style scoped>
.computed {
  width: 800px;
  display: flex;
  gap: 20px;
}
.computed div {
  flex: 1;
  background-color: antiquewhite;
}
</style>
