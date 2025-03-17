<script setup>
// ref 불러오기
import { ref } from "vue";
import Form_Ex from "./components/form_Ex.vue";
import Reservation from "./components/Reservation.vue";
const currentPage = ref("");
console.log(currentPage);
// showpage를 클릭하면 실행된다
const showPage = (page) => {
  // alert("클릭")
  // console.log(page); //page 매개변수를 지정해서 form_ex,reservation값확인
  currentPage.value = page;
  // console.log(currentPage.value)
};
</script>

<template>
  <div>
    <div class="btns">
      <!-- form_Ex,Reservation 값을 넣기 -->
      <button @click="showPage('Form_Ex')">폼 예제</button>
      <button @click="showPage('Reservation')">예약신청</button>
    </div>
    <form_Ex v-if="currentPage === 'Form_Ex'" />
    <Reservation v-if="currentPage === 'Reservation'" />
  </div>
</template>

<style scoped>
.btns {
  width: 50%;
  display: flex;
  margin: 100px auto;
}
button {
  margin: 10px;
  padding: 10px;
  width: 100%;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
}
</style>
