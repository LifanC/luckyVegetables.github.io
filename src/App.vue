<script setup>
import { ref } from 'vue'
import BunArt from './components/BunArt.vue'
const mobileOpen = ref(false)
const selected = ref('全部餐點')
const maps = 'https://www.google.com/maps?cid=14446014089504535533'
const foods = [
  {
    name: '素食水煎包',
    category: '水煎包',
    text: '一口金黃，一口滿足。把喜歡的蔬食滋味，包進日常的小確幸。',
    tag: '招牌好滋味', type: 'bun'
  },
  {
    name: '素食麵線',
    category: '麵線',
    text: '細細麵線，暖暖一碗。留一點時間，享受簡單而舒服的一餐。',
    tag: '暖心的選擇', type: 'noodle'
  },
  {
    name: '素食南部粽',
    category: '南部粽',
    text: '粽葉飄香，包起熟悉的台灣味。來一顆南部粽，享受日常的小滿足。',
    tag: '熟悉的台灣味', type: 'zongzi'
  },
  {
    name: '豆漿',
    category: '飲品',
    text: '一口豆香，簡單又滿足。搭配喜歡的餐點，享受日常的小美好。',
    tag: '豆香好滋味', type: 'soyMilk'
  }
]
const categories = ['全部餐點', ...new Set(foods.map(food => food.category))]
</script>

<template>
  <header class="header">
    <a class="brand" href="#home" aria-label="幸運蔬齋首頁">
      <img class="brand-logo" src="../img/logo.svg" alt="" width="46" height="48" />
      <span>幸運蔬齋<small>台灣小吃・素食好味</small></span>
    </a>
    <button class="mobile-toggle" @click="mobileOpen = !mobileOpen" :aria-expanded="mobileOpen"
      aria-controls="navigation" aria-label="切換導覽選單">{{ mobileOpen ? '✕' : '☰' }}
    </button>
    <nav id="navigation" :class="{ open: mobileOpen }">
      <a href="#menu" @click="mobileOpen = false">招牌餐點</a>
      <a href="#story" @click="mobileOpen = false">關於蔬齋</a>
      <a href="#visit" @click="mobileOpen = false">來店資訊</a>
      <a :href="maps" target="_blank" rel="noopener noreferrer" class="nav-cta">來找幸運 <span>↗</span></a>
    </nav>
  </header>
  <main>
    <section id="home" class="hero">
      <div class="hero-copy">
        <div class="eyebrow">
          <span></span> 好好吃飯，幸運自然來
        </div>
        <h1>一口蔬香，<br>一點
          <span class="orange">幸運</span>。
          <svg viewBox="0 0 190 20" aria-hidden="true">
            <path d="M4 12Q89 0 183 10M35 19Q95 10 153 15" />
          </svg>
        </h1>
        <p>熱騰騰的水煎包，暖心的一碗麵線。
          <br>用簡單的蔬食，陪你過有滋有味的每一天。
        </p>
        <div class="hero-actions">
          <a class="button primary" href="#menu">探索招牌餐點 <span>↗</span></a>
          <a class="text-link" href="#visit">今天，來點幸運 <span>→</span></a>
        </div>
        <div class="hero-note">
          <span class="leaf">♧</span> 素食的美好，日常就吃得到
        </div>
      </div>
      <div class="hero-visual">
        <div class="orbit"></div>
        <span class="visual-top">熱騰騰的台灣味，實實在在的好滋味。</span>
        <div class="round-stamp">蔬食日常
          <span>好運上桌</span>
          <small>用心做好味</small>
        </div>
        <BunArt />
        <span class="handwritten">幸福，就是這一口。</span>
        <span class="spark spark-one">✳</span>
        <span class="spark spark-two">✧</span>
        <div class="food-caption"><span>01 / 我們的招牌</span>
          <strong>金黃水煎包</strong>
          <i>外酥・內軟・蔬香</i>
        </div>
      </div>
      <a href="#menu" class="scroll-cue">往下探索 <span>↓</span></a>
    </section>
    <div class="ticker" aria-hidden="true">
      <span>一口蔬香</span> ✳ 
      <span>好食・好心情</span> ✳ 
      <span>幸運蔬齋</span> ✳ 
    </div>
    <section id="menu" class="section menu-section">
      <div class="section-heading">
        <div>
          <div class="eyebrow">招牌餐點</div>
          <h2>每一樣，都很滿足。</h2>
        </div>
        <p>熟悉的台灣味，多一份蔬食的美好。
          <br>今天的好心情，從這裡開始。
        </p>
      </div>
      <div class="filters" aria-label="餐點分類">
        <button v-for="category in categories" :key="category"
          :class="{ active: selected === category }" :aria-pressed="selected === category"
          @click="selected = category">{{ category }} 
          <span>
            {{ String(foods.filter(food => category === '全部餐點' || food.category === category).length).padStart(2, '0') }}
          </span>
        </button>
      </div>
      <div class="food-grid">
        <article v-for="food in foods.filter(item => selected === '全部餐點' || item.category === selected)"
          :key="food.name" class="food-card">
          <div class="food-image" :class="{ bun: food.type === 'bun' }">
            <span class="food-tag">{{ food.tag }}</span>
            <BunArt :type="food.type" loading="lazy" />
          </div>
          <div class="food-info">
            <div class="food-title">
              <h3>{{ food.name }}</h3>
              <span>↗</span>
            </div>
            <p>{{ food.text }}</p>
          </div>
        </article>
      </div>
      <p class="menu-note">餐點品項、價格與供應情況，請以店家現場資訊為準。</p>
    </section>
    <section id="story" class="story">
      <div class="story-art">
        <span class="story-circle"><img src="../img/logo.svg" alt="" /></span>
        <span class="story-seal">一日一餐
          <br>一點幸運</span>
        <span class="story-art-caption">熟悉的台灣味，吃飽也吃好。</span>
      </div>
      <div class="story-copy">
        <div class="eyebrow">關於蔬齋</div>
        <h2>把平凡的一餐，
          <br>變成日常的小幸運。
        </h2>
        <p>幸福不一定很複雜。
          <br>有時，是手裡一顆溫熱的水煎包；
          <br>有時，是忙碌之後，好好坐下吃一碗麵線。
        </p>
        <p>幸運蔬齋，讓蔬食成為親切的日常。
          <br>無論你本來就愛吃素，還是今天想換個口味，
          <br>都歡迎來這裡，吃一頓簡單、舒服的飯。</p>
          <span class="story-sign">好好吃飯，就是一件幸運的事。</span>
      </div>
    </section>
    <section id="visit" class="section visit">
      <div>
        <div class="eyebrow">來店資訊</div>
        <h2>下一站，幸運蔬齋。</h2>
        <p>想吃點簡單的，就往這裡走。
          <br>打開 Google 地圖，找到今天的小幸運。
        </p>
        <a :href="maps" class="button primary" target="_blank" rel="noopener noreferrer">開啟 Google 地圖 
          <span>↗</span>
        </a>
        <small class="visit-note">詳細地址與營業時間，請查看店家 Google
          地圖資訊。
        </small>
      </div>
      <div class="map-card">
        <iframe
          class="map-embed"
          src="https://maps.google.com/maps?cid=14446014089504535533&output=embed"
          title="幸運蔬齋 Google 地圖"
          loading="lazy"
          referrerpolicy="no-referrer-when-downgrade"
          allowfullscreen
        ></iframe>
      </div>
    </section>
  </main>
  <footer>
    <a class="brand" href="#home">
      <img class="brand-logo" src="../img/logo.svg" alt="" width="46" height="48" />
      <span>幸運蔬齋
        <small>台灣小吃・素食好味</small>
      </span>
    </a>
    <p>一口蔬香，一點幸運。</p>
    <small>© {{ new Date().getFullYear() }} 幸運蔬齋</small>
    <a href="#home" class="back-top" aria-label="回到頁首">↑</a>
  </footer>
</template>
