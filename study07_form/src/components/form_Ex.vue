<script setup>
import { ref } from "vue";

const favoriteColor = ref("");
//
const agree = ref(false);
const selectedFruits = ref([]);
const selectedCity = ref("");
const seclectedHobbies = ref([]);
</script>

<template>
  <div class="radio-group">
    <p>🎨 좋아하는 색상을 선택하세요:</p>
    <label class="raido-label">
      <input type="radio" v-model="favoriteColor" value="빨강" />
      <span class="custom-radio"></span>
      빨강
    </label>
    <label class="raido-label">
      <input type="radio" v-model="favoriteColor" value="파랑" />
      <span class="custom-radio"></span>
      파랑
    </label>
    <label class="raido-label">
      <input type="radio" v-model="favoriteColor" value="초록" />
      <span class="custom-radio"></span>
      초록
    </label>
    <p>
      ✅ 선택한 색상:<strong>{{ favoriteColor }}</strong>
    </p>
  </div>

  <div class="radio-group">
    <!-- 예제 1 : 단일 체크박스(블리언값) -->
    <h2>예제 1 : 단일 체크박스(블리언 값)</h2>
    <label>
      <input type="checkbox" v-model="agree" />
      약관에 동의 합니다.
    </label>
    <p>동의 여부: {{ agree }}</p>
    <!-- 예제 2 : 여러 체크박스(배열 저장) -->
    <h2>예제 2 : 여러 체크박스(배열 저장)</h2>
    <div class="checkbox-group">
      <p>🍴 좋아하는 과일을 선택하세요:</p>
      <label class="checkbox-label">
        <input type="checkbox" v-model="selectedFruits" value="사과" />
        <span class="custom-checkbox"></span>
        🍏사과
      </label>
      <label class="checkbox-label">
        <input type="checkbox" v-model="selectedFruits" value="포도" />
        <span class="custom-checkbox"></span>
        🍇포도
      </label>
      <label class="checkbox-label">
        <input type="checkbox" v-model="selectedFruits" value="딸기" />
        <span class="custom-checkbox"></span>
        🍓딸기
      </label>
      <label class="checkbox-label">
        <input type="checkbox" v-model="selectedFruits" value="복숭아" />
        <span class="custom-checkbox"></span>
        🍑복숭아
      </label>
      <p>
        ✔ 선택한 과일 : <strong>{{ selectedFruits }}</strong>
      </p>
    </div>
  </div>

  <div class="radio-group">
    <!--🎯 셀렉트 박스 값 바인딩 🎯 -->
    <h1>🎯 셀렉트 박스 값 바인딩 🎯</h1>
    <!-- 예제 1 : 단일 선택 -->
    <h2>예제 1 : 단일 선택</h2>
    <div class="select-group">
      <p>🏙 도시를 선택하세요:</p>
      <select class="custom-select" v-model="selectedCity">
        <!-- 옵션선택 빈배열의 내용과 비활성화 시키기 -->
        <option value="" select disabled>도시를 선택하삼💭</option>
        <option value="서울">서울</option>
        <option value="대구">대구</option>
        <option value="부산">부산</option>
      </select>
      <p>
        ✔ 선택한 도시 : <strong>{{ selectedCity }}</strong>
      </p>
    </div>
    <!-- 예제 2 : 다중 선택(배열로 저장) -->
    <h2>예제 2: 다중 선택 (배열로 저장)</h2>
    <p>취미를 선택하세요 (Ctrl 또는 Shift 키를 누르고 여러 개 선택 가능):</p>
    <select class="custom-select" v-model="seclectedHobbies"  multiple>
      <option value="독서">독서📚</option>
      <option value="수영">수영🏊‍♀️</option>
      <option value="음악감상">음악감상🎧</option>
      <option value="수면">수면😴</option>
    </select>
    <p>선택한 취미 : {{ seclectedHobbies }}</p>
  </div>
</template>

<style scoped>
.radio-group {
  padding: 10px;
  border-radius: 8px;
  border: 1px solid #ddd;
}
.raido-label,
.checkbox-label {
  display: flex;
  align-content: center;
  display: flex;
  align-items: center;
  gap: 8px;
  cursor: pointer;
  font-size: 16px;
  margin: 5px 0;
}
.raido-label input,
.checkbox-label input {
  display: none;
}
.custom-radio {
  width: 10px;
  height: 10px;
  border: 2px solid gray;
  border-radius: 50%;
  display: inline-block;
  position: relative;
}
.raido-label input:checked + .custom-radio {
  border-color: pink;
  background-color: pink;
}
.custom-checkbox {
  width: 16px;
  height: 16px;
  border: 2px solid gray;
  display: inline-block;
  position: relative;
  border-radius: 50%;
}
.checkbox-label input:checked + .custom-checkbox {
  background-color: red;
  border: red;
  position: relative;
}
.checkbox-label input:checked + .custom-checkbox::after {
  content: "✔";
  color: #fff;
  position: absolute;
  top: -5px;
  left: 3px;
}
.custom-select {
  padding: 5px 10px;
  font-size: 16px;
  border: 2px solid gray;
  border-radius: 5px;
  background-color: #fff;
  cursor: pointer;
  transition: all 0.3s;
}
.custom-select:focus {
  border-color: red;
  outline: none;
  box-shadow: 0 0 5px rgba(0, 0, 0, 0.2);
}
</style>
