<script setup>
import { ref } from "vue";
// 탭 목록 저장
const tabs = ref(["회사 소개", "서비스", "연락처", "예약 방법", "예약하기"]);
const activeTab = ref(0);
</script>
<template>
  <div class="company-container">
    <!-- 탭 버튼 -->
    <div class="tabs">
      <button
        v-for="(tab, index) in tabs"
        :key="index"
        @click="
          activeTab = index;
          console.log(activeTab, tab);
        "
        :class="{ active: activeTab === index }">
        {{ tab }}
      </button>
    </div>
    <!-- 탭 내용 -->
    <div class="tab-content">
      <section v-if="activeTab === 0">회사 소개</section>
      <section v-if="activeTab === 1">서비스 소개</section>
      <section v-if="activeTab === 2">연락처</section>
      <section v-if="activeTab === 3">예약 방법</section>
      <section v-if="activeTab === 4">예약 하기</section>
    </div>
  </div>
</template>

<style>
/* === 탭 스타일 === */
.tabs {
  display: flex;
  justify-content: space-around;
  background: var(--primary-color);
  border-radius: var(--border-radius) var(--border-radius) 0 0;
  padding: 10px;
}
.tabs button {
  flex: 1;
  padding: 12px;
  background: var(--primary-color);
  border: none;
  color: var(--white);
  font-size: 16px;
  cursor: pointer;
  transition: background 0.3s, color 0.3s;
}
.tabs button.active {
  background: var(--accent-color);
}
</style>
