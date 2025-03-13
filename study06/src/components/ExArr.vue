<script setup>
import { ref } from "vue";
import TodoList from "./TodoList.vue";
import ExArr_ex from "./ExArr_ex.vue";
// todolist 보이게하기
const showTodoList = ref(false);
const showArr = ref(false)
</script>
<template>
  <div class="wrap">
    <!-- 1.todolist -->
    <div class="container">
      <h1>TodoList Ex</h1>
      <button @click="showTodoList = !showTodoList">
        {{ showTodoList ? "닫기" : "TodoList 보기"}}
      </button>
      <TodoList v-if="showTodoList"/>
    </div>
    <hr />
    <!-- 2.배열 Array -->
    <div class="container">
      <h1>Array 공부</h1>
      <button @click="showArr = !showArr">
      {{ showArr ? "닫기" : "array 공부 보기" }}
      </button>
      <ExArr_ex v-if="showArr" />
    </div>
  </div>
</template>
<style scoped>
.wrap {
  background-color: rgb(255, 227, 232);
  display: flex;
  justify-content: center;
}
.container {
  flex: 1;
  text-align: center;
}
</style>
