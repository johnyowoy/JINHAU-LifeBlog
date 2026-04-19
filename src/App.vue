<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <nav class="main-nav">
    <div class="logo-container">
      <img src="@/assets/PianoIcon.png" alt="Logo" class="nav-logo" />
      <div class="logo-text">JINHAU LIFE</div>
    </div>
    
    <div class="links">
      <RouterLink to="/">首頁</RouterLink>
      <RouterLink to="/about">關於</RouterLink>
    </div>
  </nav>

  <RouterView />
</template>

<style>
/* 讓 Logo 容器變成水平排列 */
.logo-container {
  display: flex;
  align-items: center;
  gap: 12px; /* 圖片跟文字的間距 */
}

/* 設定圖片的大小與圓角 (二次元頭像感) */
.nav-logo {
  width: 40px;
  height: 40px;
  border-radius: 50%; /* 圓形 */
  border: 2px solid #ff7e5f; /* 給它一個夕陽橘邊框 */
  object-fit: cover; /* 避免圖片變形 */
}

.logo-text {
  color: #ff7e5f;
  font-weight: bold;
  font-size: 1.5rem;
  letter-spacing: 2px;
}
/* 1. 全域重置：消除預設的邊距 */
body {
  margin: 0;
  padding: 0;
  font-family: 'PingFang TC', 'Microsoft JhengHei', sans-serif;
  background-color: #1a1a1a; /* 給一個深色底，避免閃白 */
}

/* 2. 導覽列樣式：讓它漂浮在最上面 */
.main-nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem 2rem;
  background: rgba(0, 0, 0, 0.8);
  backdrop-filter: blur(10px);
  position: sticky;
  top: 0;
  z-index: 100;
}

.logo {
  color: #ff7e5f;
  font-weight: bold;
  font-size: 1.5rem;
  letter-spacing: 2px;
}

.links a {
  color: white;
  text-decoration: none;
  margin-left: 20px;
  font-weight: 500;
  transition: color 0.3s;
}

.links a:hover, .links a.router-link-active {
  color: #feb47b;
}

/* 移除原本 Vue 預設可能干擾的佈局 */
#app {
  max-width: 100% !important;
  margin: 0 !important;
  padding: 0 !important;
  display: block !important;
}
</style>