<script setup>
import { ref } from "vue";
//------ 1.버튼 클릭 이벤트
const count = ref(0);
//------ 2.입력 이벤트
// 입력된 메시지를 저장하는 변수 = 'message'
const message = ref("");
//------ 3.마우스 오버 이벤트
// ref(false) : 마우스에다가 거짓을 담아놨다
const hover = ref(false);
//------ 4.키보드 이벤트
// newMessage = 키보드 이벤트에서 입력된 메시지
const newMessage = ref("");
// addMesagge = 추가된 메시지를 저장하는 배열
const messages = ref([]); //li가 있기때문에 배열안에 넣기위해 [] 사용
const addMessage = () => {
  if (newMessage.value) {
    messages.value.push(newMessage.value);
    // 입력창 초기화
    newMessage.value = true;
  }
};
//------ 5.폼 제출
const userName = ref("");
const saveName = ref("");
// 폼 제출 기능
const submitForm = () => {
  //userName의 값을 saveName에게 할당하여 출력되게함
  saveName.value = userName.value;
};
//------ 6.더블클릭 이벤트
const color = ref("lightgray");
// ~행동을 할것이다 : =() => {}
const toggleColor = () => {
  color.value = color.value === "lightgray" ? "skyblue" : "lightgray";
};
//------ 7.마우스 위치 추적
const x = ref(0);
const y = ref(0);
// 마우스 위치 업데이트 함수
const updatePosition = (event) => {
  x.value = event.clientX;
  y.value = event.clientY;
};
//------ 8.체크박스
const checked = ref(false);
// ------ 9.컨텍스트 메뉴
const menuVisible = ref(false);
const menuX = ref(0);
const menuY = ref(0);
const showMenu = (event) => {
  menuVisible.value = true;
  menuX.value = event.clientX;
  menuY.value = event.clientY;
};
// option 클릭시 알림팝업창 보임
const selectOption = (option) => {
  // console.log(option);
  alert(`${option} 선택됨`);
  menuVisible.value = false;
};
</script>

<template>
  <div class="container">
    <h1>vue event</h1>
    <!-- 1.버튼 클릭 이벤트 -->
    <button @click="count++">클릭 {{ count }} 번</button><br />
    <!-- 2.입력 이벤트 -->
    <!-- v-model에 변수명 'message'지정 -->
    <input type="text" placeholder="입력하세요." v-model="message" />
    <p>입력값 출력: {{ message }}</p>
    <!--클릭 횟수출력-->
    <!-- 3.마우스 오버 이벤트 -->
    <button
      @mouseover="hover = true"
      @mouseleave="hover = false"
      :style="{ backgroundColor: hover ? 'pink' : 'gray', color: hover ? 'gray' : 'pink' }">
      마우스를 올리면 색상 변경됨 ! 🖱</button
    ><br />
    <!-- 4.키보드 이벤트 -->
    <!-- enter 누를때 입력+출력됨 -->
    <input type="text" placeholder="Enter시 입력값 출력⌨" v-model="newMessage" @keyup.enter="addMessage" />
    <ul>
      <li v-for="(msg, index) in messages" :key="index">{{ msg }}</li>
    </ul>
    <!-- 5.폼 제출 -->
    <!-- 폼 제출하면 username 값을 saveName에 저장하고 경고창을 띄움 -->
    <form @submit.prevent="submitForm">
      <!--prevent 없으면 저장이 안됨-->
      <input type="text" placeholder="이름 입력" v-model="userName" />
      <button type="submit">제출</button>
    </form>
    <p>입력된 이름: {{ saveName }}</p>
    <!-- 6.더블클릭 이벤트 -->
    <div class="box" :style="{ backgroundColor: color }" @dblclick="toggleColor">더블 클릭하면 색상바뀜 ! 🎵</div>

    <!-- 7.마우스 위치 추적 -->
    <div @mousemove="updatePosition" class="tracker">X: {{ x }} , Y: {{ y }}</div>
    <!-- 8.체크박스 -->
    <label>
      <input type="checkbox" v-model="checked" />
      동의합니다.
    </label>
    <p>{{ checked ? "동의 하셨습니다." : "동의가 필요합니다." }}</p>
    <!-- 9. 컨텍스트 메뉴 : 우클릭 했을때 메뉴 나오게하기-->
    <div class="box" @contextmenu.prevent="showMenu($event)">우클릭하면 옵션메뉴나옴</div>
    <ul v-if="menuVisible" :style="{ top: `${menuY}px`, left: `${menuX}px` }" class="context-menu">
      <li @click="selectOption('옵션1')">옵션 1</li>
      <li @click="selectOption('옵션2')">옵션 2</li>
    </ul>
  </div>
</template>

<style scoped>
/* 6. 더블클릭 이벤트 */
.box {
  position: relative;
  width: 200px;
  height: 100px;
  border: 1px solid #333;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: rgb(255, 255, 191);
}
/* 7.마우스 위치 추적 박스 */
.tracker {
  width: 100%;
  height: 100px;
  border: 1px solid #333;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: paleturquoise;
}
/* 9.컨텍스트 메뉴 */
.context-menu {
  position: absolute;
  background-color: #fff;
  border: 1px solid #ccc;
  list-style: none;
  padding: 5px;
}
.context-menu li {
  padding: 5px;
  cursor: pointer;
}
.context-menu li:hover {
  background-color: antiquewhite;
}
</style>
