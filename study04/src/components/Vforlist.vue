<script setup>
import { ref, reactive } from "vue";
//1, 2
const items = ref([
  { message: "Foo", children: ["A", "B"] },
  { message: "Bar", children: ["C", "D"] },
]);
const parentTxt = ref("Parent");

// 3. 구조 분해 할당
const user = {
  name: "홍길동",
  age: 25,
  job: "개발자",
};
//기존 방식
console.log(user.name); //홍길동
console.log(user.age); //25

// 구조분해 할당 방식 . .
const { name, age } = user;
console.log(name); //홍길동

// 5
const myObject = reactive({
  title: "Vue에서 목록을 작성하는 방법",
  author: "홍길동",
  publishedAt: "2016-04-10",
});

// 9
// 할 일 목록 (isComplete 값에 따라 완료 여부 결정)
const todos = ref([
  { name: "청소하기", isComplete: false },
  { name: "공부하기", isComplete: true },
  { name: "운동하기", isComplete: false },
]);
</script>
<template>
  <div>
    <h3>Vforlist.vue</h3>
    <!-- 1 -->
    <h4>1. 기본 리스트 반복</h4>
    <ul>
      <li v-for="(item, index) in items" :key="item.message">
        {{ item.message }}
        <ul>
          <li v-for="(child, index) in item.children" :key="child">
            {{ child }}
          </li>
        </ul>
      </li>
    </ul>
    <hr />
    <!-- 2 -->
    <h4>2. index 같이 출력하기</h4>
    <ul>
      <li v-for="(item, index) in items" :key="index">
        {{ parentTxt }} - {{ index + 1 }} - {{ item.message }}
      </li>
    </ul>
    <hr />
    <!-- 3 -->
    <h4>3. 구조 분해 할당하기</h4>
    <ul>
      <li v-for="{ message } in items" :key="message">
        {{ message }}
      </li>
    </ul>
    <hr />
    <!-- 4 -->
    <h4>4. 중첩 반복</h4>
    <ul>
      <!-- 부모요소반복 -->
      <li v-for="item in items" :key="item.message">
        {{ item.message }}
        <!-- 자식 요소 반복 -->
        <p v-for="child in item.children" :key="child">
          {{ item.message }} - {{ child }}
        </p>
      </li>
    </ul>
    <hr />
    <!-- 5 -->
    <h4>5. 객체 반복하기</h4>
    <ul>
      <!-- 객체의 key(), value() 반복 -->
      <li v-for="(value, key) in myObject" :key="key">
        {{ key }} : {{ value }}
      </li>
    </ul>
    <hr />
    <!-- 6 -->
    <h4>6. 객체 반복 + 인덱스</h4>
    <ul>
      <li v-for="(value, key, index) in myObject" :key="index">
        {{ index + 1 }}. {{ key }} : {{ value }}
      </li>
    </ul>
    <hr />
    <!-- 7 -->
    <h4>7. 특정 수 반복</h4>
    <ul>
      <!-- 1~5 반복 -->
      <li v-for="number in 5" :key="number">{{ number }}</li>
    </ul>
    <hr />
    <!-- 8 -->
    <h4>8. 템플릿 사용하기</h4>
    <ul>
      <template v-for="item in items" :key="item">
        <li>
          {{ item.message }}
        </li>
      </template>
    </ul>
    <hr />
    <!-- 9 -->
    <h4>9. 조건부 렌더링과 함께 사용</h4>
    <ul>
      <template v-for="todo in todos">
        <li>{{ todo.name }}</li>
        <li v-if="!todo.isComplete" :key="todo">
          {{ todo.isComplete }}
        </li>
        <br />
      </template>
    </ul>
    <hr />
    <!-- 10 -->
    <h4>10.템플릿을 활용한 조건부 렌더링</h4>
    <ul>
      <template v-for="todo in todos" >
        <li v-if="!todo.isComplete" :key="todo.name">{{ todo.name }}</li>
      </template>
    </ul>
    <hr>
    <!-- 11 -->
    <h4>11. :key속성 </h4>
    <ul>
        <!-- div태그를 사용해 반복되는 리스트 출력 -->
        <div v-for="item in items" :key="item.message">
            {{ item.message }}
        </div>
        <span v-for="item in items" :key="item.message">
            {{ item.message }}
        </span>
    </ul>

  </div>
</template>
<style scoped></style>
