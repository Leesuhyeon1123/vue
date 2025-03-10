<script setup>
import { ref } from "vue";
// v-if, v-show
const isVisible = ref(true);
//전환
const nice = ref(true);
//ABC
const type1 = ref("A");
// 단락표시
const ok = ref(true);
//로그인 예약 어쩌구
const isLogin = ref(false);
const toggleLogin = () => {
  isLogin.value = !isLogin.value;
};
// 예약 가능?
const isAvailable = ref(true);
// 예약 날짜 선택
const selectDate = ref("");
</script>

<template>
  <div class="box">
    <!-- v-if, v-show -->
    <div class="if-show">
      <h2>V-if, V-show</h2>
      <hr>
      <button @click="isVisible = !isVisible">지수언니🌸</button>
      <p v-if="isVisible">
        V-if: 조건 true일 때 나와여 (조건이 false면 Dom에서 완전히 제거됨.)
      </p>
      <p v-show="isVisible">
        V-show: 조건에 따라 보이기만 함 (조건이 false여도 dom에서 남아있는데 안
        보이는 거임)
      </p>
    </div>
    <hr />
    <!-- 전환 -->
    <div class="if">
      <button @click="nice = !nice">전환</button>
      <h4 v-if="nice">🍀</h4>
      <h4 v-else>🌸</h4>
    </div>
    <hr />
    <!-- ABC -->
    <div class="filese">
      <div v-if="type1 === 'A'">🍿</div>
      <div v-else-if="type1 === 'B'">🥐</div>
      <div v-else-if="type1 === 'C'">🥯</div>
      <div v-else>식빵</div>
      <br />
      <button @click="type1 = 'A'">🍿</button>
      <button @click="type1 = 'B'">🥐</button>
      <button @click="type1 = 'C'">🥯</button>
      <button @click="type1 = 'D'">🍞</button>
    </div>
    <hr />
    <!-- 단락 -->
    <button @click="ok = !ok">🌼</button>
    <div v-if="ok">
      <h3 class="info">제목</h3>
      <p>단락 1</p>
      <p>단락 2</p>
    </div>
    <hr />
    <!-- 로그인 상태에 따라서 예약버튼 보이기 -->
    <div>
      <button @click="toggleLogin">
        {{ isLogin ? "💛" : "🖤" }}
      </button>
      <br />
      <b v-if="isLogin">하이 💛</b>
      <b v-else>바이 🖤</b>
    </div>
    <hr />
    <!-- 예약 가능 여부에 따라서 버튼 다르게 보이기 -->
    <div class="container">
      <h4>예약 ㄱㄴ ?</h4>
      <!-- 객체 문법 (:class="{ '클래스명1': 조건1, '클래스명2': 조건2 }) -->
      <p :class="{ available: isAvailable, unavailble: !isAvailable }">
        {{ isAvailable ? "ㅇㅇ" : "ㄴㄴ" }}
      </p>
      <button
        @click="isAvailable = !isAvailable"
        :class="{ available: isAvailable, unavailble: !isAvailable }"
      >
        {{ isAvailable ? "ㄱㄱ" : "ㅠㅠ" }}
      </button>
    </div>
    <hr />
    <!-- 예약 날짜 선택  -->
    <div class="dateBox">
      <h4>예약 날짜💌</h4>
      <input type="date" class="date-input" v-model="selectDate" />
      <p :class="{ selected: selectDate, unselected: !selectDate }">
        {{ selectDate ? `예약 : ${selectDate} 임` : "날짜 선택하세용" }}
      </p>
    </div>
  </div>
</template>

<style scoped>
h2 {
  background-color: pink;
}
.info {
  background-color: pink;
}
button {
  padding: 6px 12px;
  font-size: 16px;
  margin: 0 10px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background 0.3s, transform 0.2s;
  background-color: rgb(0, 150, 125);
  color: #fff;
}
.available {
  color: lightblue;
}
.available:hover {
  color: rgb(0, 0, 0);
}
.unavailble {
  color: pink;
  cursor: not-allowed;
}
.date-input {
  padding: 10px;
  font-size: 16px;
  border-radius: 5px;
  border: 1px solid #ccc;
  outline: none;
  transition: all 0.3s;
}
.date-input:focus {
  border-color: blue;
}
.selected {
  color: darkgreen;
  font-weight: bold;
}
.unselected {
  color: red;
}
</style>
