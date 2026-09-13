<script setup>
import { ref } from 'vue'
import BunArt from './components/BunArt.vue'
const mobileOpen = ref(false)
const selected = ref('全部餐點')
const maps = 'https://www.google.com/maps?cid=14446014089504535533'
const foods = [
  {
    name: '素食水煎包',
    en: 'PAN-FRIED VEGETARIAN BUNS',
    category: '水煎包',
    text: '一口金黃，一口滿足。把喜歡的蔬食滋味，包進日常的小確幸。',
    tag: '招牌好滋味', bowl: false
  },
  {
    name: '素食麵線',
    en: 'VEGETARIAN VERMICELLI',
    category: '麵線',
    text: '細細麵線，暖暖一碗。留一點時間，享受簡單而舒服的一餐。',
    tag: '暖心的選擇', bowl: true
  }
]
</script>

<template>
  <header class="header">
    <a class="brand" href="#home" aria-label="幸運蔬齋首頁"><span
        class="brand-mark">幸<span>✳</span></span><span>幸運蔬齋<small>LUCKY VEGETABLES</small></span></a>
    <button class="mobile-toggle" @click="mobileOpen = !mobileOpen" :aria-expanded="mobileOpen"
      aria-controls="navigation" aria-label="切換導覽選單">{{ mobileOpen ? '✕' : '☰' }}</button>
    <nav id="navigation" :class="{ open: mobileOpen }"><a href="#menu" @click="mobileOpen = false">招牌餐點</a><a
        href="#story" @click="mobileOpen = false">關於蔬齋</a><a href="#visit" @click="mobileOpen = false">來店資訊</a><a
        :href="maps" target="_blank" rel="noopener noreferrer" class="nav-cta">來找幸運 <span>↗</span></a></nav>
  </header>
  <main>
    <section id="home" class="hero">
      <div class="hero-copy">
        <div class="eyebrow"><span></span> 好好吃飯，幸運自然來</div>
        <h1>一口蔬香，<br>一點<span class="orange">幸運</span>。<svg viewBox="0 0 190 20" aria-hidden="true">
            <path d="M4 12Q89 0 183 10M35 19Q95 10 153 15" />
          </svg></h1>
        <p>熱騰騰的水煎包，暖心的一碗麵線。<br>用簡單的蔬食，陪你過有滋有味的每一天。</p>
        <div class="hero-actions"><a class="button primary" href="#menu">探索招牌餐點 <span>↗</span></a><a class="text-link"
            href="#visit">今天，來點幸運 <span>→</span></a></div>
        <div class="hero-note"><span class="leaf">♧</span> 素食的美好，日常就吃得到</div>
      </div>
      <div class="hero-visual">
        <div class="orbit"></div><span class="visual-top">SIMPLE FOOD. LITTLE JOYS.</span>
        <div class="round-stamp">蔬食日常<span>好運上桌</span><small>MADE WITH LOVE</small></div>
        <BunArt /><span class="handwritten">幸福，就是這一口。</span><span class="spark spark-one">✳</span><span
          class="spark spark-two">✧</span>
        <div class="food-caption"><span>01 / 我們的招牌</span><strong>金黃水煎包</strong><i>外酥・內軟・蔬香</i></div>
      </div>
      <a href="#menu" class="scroll-cue">往下探索 <span>↓</span></a>
    </section>
    <div class="ticker" aria-hidden="true"><span>一口蔬香</span> ✳ <span>A LITTLE BITE OF LUCK</span> ✳ <span>好食・好心情</span>
      ✳ <span>幸運蔬齋</span> ✳ <span>A LITTLE BITE OF LUCK</span> ✳</div>
    <section id="menu" class="section menu-section">
      <div class="section-heading">
        <div>
          <div class="eyebrow">OUR SIGNATURES / 招牌餐點</div>
          <h2>簡單兩樣，就很滿足。</h2>
        </div>
        <p>熟悉的台灣味，多一份蔬食的美好。<br>今天的好心情，從這裡開始。</p>
      </div>
      <div class="filters" aria-label="餐點分類"><button v-for="category in ['全部餐點', '水煎包', '麵線']" :key="category"
          :class="{ active: selected === category }" :aria-pressed="selected === category"
          @click="selected = category">{{ category }} <span>{{ category === '全部餐點' ? '02' : '01' }}</span></button>
      </div>
      <div class="food-grid">
        <article v-for="food in foods.filter(item => selected === '全部餐點' || item.category === selected)"
          :key="food.name" class="food-card">
          <div class="food-image" :class="{ noodle: food.bowl }"><span class="food-tag">{{ food.tag }}</span>
            <BunArt :bowl="food.bowl" /><span class="image-label">餐點插畫示意</span>
          </div>
          <div class="food-info">
            <div class="food-title">
              <h3>{{ food.name }}</h3><span>↗</span>
            </div><small>{{ food.en }}</small>
            <p>{{ food.text }}</p>
          </div>
        </article>
      </div>
      <p class="menu-note">餐點品項、價格與供應情況，請以店家現場資訊為準。</p>
    </section>
    <section id="story" class="story">
      <div class="story-art"><span class="story-circle">蔬</span><span class="story-seal">一日一餐<br>一點幸運</span><span
          class="story-art-caption">GOOD FOOD, GOOD MOOD.</span></div>
      <div class="story-copy">
        <div class="eyebrow">OUR PHILOSOPHY / 關於蔬齋</div>
        <h2>把平凡的一餐，<br>變成日常的小幸運。</h2>
        <p>幸福不一定很複雜。<br>有時，是手裡一顆溫熱的水煎包；<br>有時，是忙碌之後，好好坐下吃一碗麵線。</p>
        <p>幸運蔬齋，讓蔬食成為親切的日常。<br>無論你本來就愛吃素，還是今天想換個口味，<br>都歡迎來這裡，吃一頓簡單、舒服的飯。</p><span
          class="story-sign">好好吃飯，就是一件幸運的事。</span>
      </div>
    </section>
    <section id="visit" class="section visit">
      <div>
        <div class="eyebrow">COME SAY HELLO / 來店資訊</div>
        <h2>下一站，幸運蔬齋。</h2>
        <p>想吃點熱的，就往這裡走。<br>打開 Google 地圖，找到今天的小幸運。</p><a :href="maps" class="button primary" target="_blank"
          rel="noopener noreferrer">開啟 Google 地圖 <span>↗</span></a><small class="visit-note">詳細地址與營業時間，請查看店家 Google
          地圖資訊。</small>
      </div><a :href="maps" class="map-card" target="_blank" rel="noopener noreferrer" aria-label="前往幸運蔬齋 Google 地圖">
        <div class="map-water"></div>
        <div class="road road-one"></div>
        <div class="road road-two"></div>
        <div class="road road-three"></div>
        <div class="map-marker">✳<span>幸運蔬齋<small>你的小幸運，在這裡。</small></span></div><span class="map-bottom">位置示意 <span>在
            Google 地圖中查看 ↗</span></span>
      </a>
    </section>
  </main>
  <footer><a class="brand" href="#home"><span class="brand-mark">幸<span>✳</span></span><span>幸運蔬齋<small>LUCKY
          VEGETABLES</small></span></a>
    <p>一口蔬香，一點幸運。</p><small>© {{ new Date().getFullYear() }} 幸運蔬齋</small><a href="#home" class="back-top"
      aria-label="回到頁首">↑</a>
  </footer>
</template>
