<script setup>
import { ref } from 'vue'

// 1. 用 Vue 的響應式變數來控制是否激活效果
const isActivated = ref(false)

// 2. 定義滑鼠移入與移出的函式
function activateMiracle() {
  isActivated.value = true
}

function deactivateMiracle() {
  isActivated.value = false
}
</script>

<template>
  <div class="about-container" :class="{ 'is-colorful': isActivated }">
    <div class="miracle-wrapper">
      <h1 
        class="miracle-text"
        @mouseover="activateMiracle"
        @mouseleave="deactivateMiracle"
      >
        <span>2018年，</span><br>
        <span>我遇見了</span><br>
        <span class="highlight">【你的名字】、</span><br>
        <span class="highlight">【遊戲人生】，</span><br>
        <span>從此沉入二次元的世界。</span>
      </h1>
      
      <div v-if="isActivated" class="fireworks-container">
        <div v-for="n in 12" :key="n" class="sparkle"></div>
      </div>
    </div>
  </div>
</template>

<style scoped>
/* A. 初始黑白狀態 */
.about-container {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #1a1a1a; /* 純黑背景 */
  transition: background 1s ease; /* 背景切換動畫 */
  overflow: hidden; /* 避免煙火跑出去 */
  font-family: 'PingFang TC', 'Microsoft JhengHei', sans-serif;
}

.miracle-wrapper {
  position: relative;
  text-align: center;
  padding: 20px;
}

.miracle-text {
  font-size: 2.5rem;
  color: #666; /* 初始灰色文字 */
  line-height: 1.6;
  font-weight: bold;
  cursor: pointer;
  transition: all 0.5s cubic-bezier(0.68, -0.55, 0.27, 1.55); /* 放大與變形動畫 */
  text-shadow: 0 0 10px rgba(255, 255, 255, 0);
}

.miracle-text span {
  display: inline-block; /* 讓每個 span 獨立運動 */
  transition: all 0.3s ease;
}

/* B. 彩色與放大狀態 */
.is-colorful {
  /* 《你的名字》黃昏漸層背景 */
  background: linear-gradient(135deg, #2c3e50 0%, #ff7e5f 50%, #feb47b 100%);
}

.is-colorful .miracle-text {
  color: white;
  transform: scale(1.15) rotate(-2deg); /* 放大並輕微旋轉 */
  text-shadow: 0 0 20px rgba(255, 255, 255, 0.8), 0 0 40px #ff7e5f;
}

/* 讓 highlight 的文字變成漸層彩色 (遊戲人生風格) */
.is-colorful .miracle-text .highlight {
  background: linear-gradient(to right, #ff7e5f, #feb47b, #ff7e5f);
  -webkit-background-clip: text;
  background-clip: text;
  color: transparent;
  animation: colorWave 2s infinite linear; /* 彩色波浪動畫 */
}

/* C. 煙火星星樣式 */
.fireworks-container {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 100%;
  height: 100%;
  pointer-events: none; /* 煙火不阻擋滑鼠 */
}

.sparkle {
  position: absolute;
  width: 10px;
  height: 10px;
  background-color: #feb47b; /* 煙火顏色 */
  border-radius: 50%;
  opacity: 0;
  animation: sparkleExplode 1s ease-out forwards;
}

/* 生成不同方向與延遲的煙火 */
.sparkle:nth-child(1)  { top: 10%; left: 10%; animation-delay: 0.0s; }
.sparkle:nth-child(2)  { top: 20%; left: 80%; animation-delay: 0.1s; }
.sparkle:nth-child(3)  { top: 80%; left: 20%; animation-delay: 0.2s; }
.sparkle:nth-child(4)  { top: 70%; left: 70%; animation-delay: 0.1s; }
.sparkle:nth-child(5)  { top: 50%; left: 5%;  animation-delay: 0.3s; }
.sparkle:nth-child(6)  { top: 50%; left: 95%; animation-delay: 0.2s; }
.sparkle:nth-child(7)  { top: 10%; left: 50%; animation-delay: 0.4s; }
.sparkle:nth-child(8)  { top: 90%; left: 50%; animation-delay: 0.3s; }
.sparkle:nth-child(9)  { top: 30%; left: 30%; animation-delay: 0.5s; }
.sparkle:nth-child(10) { top: 60%; left: 40%; animation-delay: 0.4s; }
.sparkle:nth-child(11) { top: 20%; left: 60%; animation-delay: 0.6s; }
.sparkle:nth-child(12) { top: 80%; left: 90%; animation-delay: 0.5s; }

/* D. 動畫定義 (Keyframes) */

/* 文字彩色波浪動畫 */
@keyframes colorWave {
  0%   { background-position: 0% 50%; }
  100% { background-position: 100% 50%; }
}

/* 星星爆炸消失動畫 */
@keyframes sparkleExplode {
  0%   { transform: scale(0); opacity: 0; }
  10%  { transform: scale(1.5); opacity: 1; }
  100% { transform: scale(0); opacity: 0; }
}

/* 移除原本 Vue 的 CSS */
#app {
  max-width: 100% !important;
  margin: 0 !important;
  padding: 0 !important;
}
</style>