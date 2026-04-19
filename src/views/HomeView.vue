<script setup>
import { ref } from 'vue'

// 1. 你的互動點讚邏輯
const count = ref(0)
const message = ref("歡迎來到 Jinhau 二次元空間")

function increase() {
  count.value++
  if (count.value >= 20) {
    message.value = "哇！你是真愛粉！(。・ω・。)ノ♡"
  } else if (count.value >= 10) {
    message.value = "謝謝你的能量！遊戲開始！"
  }
}

// 2. 你的生活區塊資料 (這就是管理資料的地方，未來你可以改這裡就好)
const lifeSections = ref([
  {
    id: 'piano',
    icon: '🎹',
    title: '鋼琴練琴室',
    description: '讓自己放鬆，聽點琴聲',
    tag: '#音樂'
  },
  {
    id: 'game',
    icon: '🎮',
    title: '遊戲冒險紀錄',
    description: '絕區零 讚啦',
    tag: '#二次元'
  },
  {
    id: 'aivtuber',
    icon: '',
    title: 'AI vTuber',
    description: '跟主人一起耍廢廢，耶',
    tag: '#ai'
  },
  {
    id: 'jlanguage',
    icon: '📚',
    title: '日文加強計畫',
    description: '日文 N3 挑戰中',
    tag: '#學習歷程'
  },
  {
    id: 'elanguage',
    icon: '📚',
    title: '英文修練計畫',
    description: '英文多益挑戰金色',
    tag: '#學習歷程'
  }
])
</script>

<template>
  <div class="home-container">
    <header class="hero">
      <div class="hero-content">
        <h1 class="fade-in">{{ message }}</h1>
        <p class="subtitle">從 2018 年《你的名字》開始，探索鋼琴、遊戲與語言的交會點。</p>
        
        <div class="interact-box">
          <p>當前熱度：<span class="count-num">{{ count }}</span></p>
          <button @click="increase" class="like-btn">給這篇筆記一個讚 (*ゝω・)ノ</button>
        </div>
      </div>
    </header>

    <section class="content-grid">
      <div v-for="section in lifeSections" :key="section.id" class="card">
        <div class="card-icon">{{ section.icon }}</div>
        <h2>{{ section.title }}</h2>
        <p>{{ section.description }}</p>
        <span class="card-tag">{{ section.tag }}</span>
      </div>
    </section>
  </div>
</template>

<style scoped>
/* 全域容器：Kimi no Na wa 漸層背景 */
.home-container {
  min-height: 100vh;
  background: linear-gradient(135deg, #2c3e50 0%, #ff7e5f 50%, #feb47b 100%);
  color: white;
  padding: 40px 20px;
  font-family: 'PingFang TC', 'Microsoft JhengHei', sans-serif;
}

/* 英雄區樣式 */
.hero {
  text-align: center;
  padding: 60px 0;
  margin-bottom: 40px;
}

.hero h1 {
  font-size: 3rem;
  margin-bottom: 10px;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
}

.subtitle {
  font-size: 1.2rem;
  color: #f1f1f1;
  margin-bottom: 30px;
}

/* 互動區域 */
.interact-box {
  background: rgba(255, 255, 255, 0.2);
  display: inline-block;
  padding: 15px 30px;
  border-radius: 15px;
  backdrop-filter: blur(5px);
}

.count-num {
  font-size: 2rem;
  font-weight: bold;
  color: #feb47b;
}

.like-btn {
  padding: 12px 24px;
  background-color: #ff7e5f;
  color: white;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  font-weight: bold;
  transition: all 0.3s ease;
  margin-top: 10px;
}

.like-btn:hover {
  background-color: #feb47b;
  transform: translateY(-2px);
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.2);
}

/* 內容網格樣式 (v-for 生成) */
.content-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 30px;
  max-width: 1200px;
  margin: 0 auto;
}

/* 卡片樣式 */
.card {
  background: rgba(44, 62, 80, 0.6);
  padding: 30px;
  border-radius: 20px;
  backdrop-filter: blur(5px);
  border: 1px solid rgba(255, 126, 95, 0.3);
  transition: transform 0.3s ease;
  position: relative;
  overflow: hidden;
}

.card:hover {
  transform: translateY(-5px);
  border-color: #feb47b;
}

.card-icon {
  font-size: 3rem;
  margin-bottom: 15px;
}

.card h2 {
  font-size: 1.5rem;
  color: #feb47b;
  margin-bottom: 10px;
}

.card p {
  color: #d1d1d1;
  line-height: 1.6;
  margin-bottom: 20px;
}

.card-tag {
  background-color: rgba(255, 126, 95, 0.2);
  color: #ff7e5f;
  padding: 5px 12px;
  border-radius: 20px;
  font-size: 0.8rem;
  position: absolute;
  bottom: 20px;
  right: 20px;
}

/* 動畫效果 */
.fade-in {
  animation: fadeIn 1s ease;
}

@keyframes fadeIn {
  from { opacity: 0; transform: translateY(-20px); }
  to { opacity: 1; transform: translateY(0); }
}
</style>