<script setup>
// 반응형 데이터를 만들때 사용하는 vue의 함수
// 값이 바뀌면 자동으로 화면 업데이트해줌
import { onMounted, ref } from "vue";
// **ref([])**는 빈 배열을 reservations라는 변수에 할당
// **ref([])**는 마치 빈 예약장부, ref를 사용해서 자동 업데이트됨
const reservations = ref([]);
// ---------------장바구니 예제
// cartItems와 newItem은 반응형 변수. 값을 바꾸면 화면에 자동으로 반영
const cartItems = ref([]);
const newItem = ref("");
// 예약 데이터 불러오기 = fetchReservation
//   reservations.value =두개의 예약 정보를 배열에 넣는 코드, 배열저장
const fetchReservations = async () => {
  reservations.value = [
    { id: 1, name: "김철수", date: "2025-03-20", time: "14:00" },
    { id: 2, name: "이영희", date: "2025-03-22", time: "10:30" },
  ];
};
// **onMounted**는 컴포넌트가 화면에 나타날 때 실행되는 함수
onMounted(() => {
  message.value = "컴포넌트가 화면에 표시됨!";
  fetchReservations();
  //   장바구니기능
  const savedCart = localStorage.getItem("cart");
  if (savedCart) {
    cartItems.value = JSON.parse(savedCart);
  }
  //   다크모드 전환
  isDarkMode.value = window.matchMedia("(prefers-color-scheme: dark)").matches;
  //   스크롤 감지 기능
  window.addEventListener("scroll", () => {
    showTopButton.value = window.scrollY > 200;
  });
});
// 장바구니 저장 함수
const saveCart = () => {
  localStorage.setItem("cart", JSON.stringify(cartItems.value));
};
// 장바구니에 상품 추가하는 함수
const addToCart = () => {
  if (newItem.value.trim() !== "") {
    cartItems.value.push(newItem.value);
    saveCart(); // 로컬스토리지 저장
    newItem.value = ""; // 입력 필드 초기화
  }
};
// 장바구니 아이템 삭제
const removeCart = (index) => {
  cartItems.value.splice(index, 1);
  saveCart(); // 로컬스토리지 저장
};
const message = ref("로딩중...");
// 다크모드 전환
const isDarkMode = ref(false);
const toggleDarkMode = () => {
  isDarkMode.value = !isDarkMode.value;
};
// go top 버튼
const showTopButton = ref(false);
// 버튼 눌렀을때 상단으로 이동하는 함수
const scrollToTop = () => {
  window.scrollTo({ top: 0, behavior: "smooth" });
};
</script>

<template>
  <div class="container">
    <h1>OnMounted()예제</h1>
    <p>{{ message }}</p>
    <div class="reservation">
      <h2>예약목록</h2>
      <!-- 예약 목록이 보여져야함 -->
      <ul>
        <!-- v-for reservation 배열을 반복하는 구문 -->
        <!-- key는 리스트를 렌더링할 때 각 항목을 고유하게 구분, id값을 찾음-->
        <li v-for="res in reservations" :key="res.id">{{ res.name }} - {{ res.date }}({{ res.time }})</li>
      </ul>
    </div>
    <!-- 장바구니 기능 -->
    <div class="cart">
      <h2>🛒 장바구니 ({{ cartItems.length }})</h2>
      <div class="cart-btn">
        <input v-model="newItem" placeholder="상품 이름 입력" />
        <button @click="addToCart">+추가</button>
      </div>
      <ul v-if="cartItems.length">
        <li v-for="(item, index) in cartItems" :key="index">
          {{ item }}
          <button @click="removeCart(index)">❌</button>
        </li>
      </ul>
      <p v-else>장바구니가 비어 있습니다.</p>
    </div>
    <!-- 다크모드 전환 -->
    <div class="darkMode" :class="{ dark: isDarkMode }">
      <p>현재모드 : {{ isDarkMode ? "🌙 다크 모드" : "☀ 라이트 모드" }}</p>
      <button @click="toggleDarkMode">
        {{ isDarkMode ? "☀ 라이트 모드로 변경" : "🌙 다크 모드로 변경" }}
      </button>
    </div>
    <!-- gotop버튼 -->
    <button v-if="showTopButton" @click="scrollToTop" class="topBtn">🔝 TOP</button>
  </div>
</template>

<style scoped>
.container {
  width: 70%;
  height: 2000px;
  margin: 100px auto;
}
.container div {
  padding: 20px 0;
}
.cart-btn {
  display: flex;
  justify-content: space-between;
}
.container button {
  width: 20%;
  margin: 0;
}
.container input {
  width: 70%;
}
.dark {
  background-color: #333;
  color: #fff;
}
/* TOP 버튼 스타일 */
.topBtn {
  position: fixed;
  bottom: 20px;
  right: 20px;
  background: #007bff;
  color: white;
  padding: 10px 15px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}
.topBtn:hover {
  background: #0056b3;
}
</style>
