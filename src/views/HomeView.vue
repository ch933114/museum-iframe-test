<script setup lang="ts">
import { ref } from 'vue'
import { RouterLink } from 'vue-router'

const menuOpen = ref(false)

const exhibitions = [
  {
    category: '當期特展',
    title: '光的形狀',
    subtitle: '從印象派到當代的觀看練習',
    date: '2025.06.14 — 2025.10.12',
    image:
      'https://images.unsplash.com/photo-1577083552431-6e5fd01aa342?auto=format&fit=crop&w=1000&q=85',
    alt: '色彩鮮明的抽象藝術畫作',
    tone: 'terracotta',
  },
  {
    category: '典藏精選',
    title: '島嶼的記憶',
    subtitle: '在風景之中，重新認識我們',
    date: '2025.05.03 — 2025.09.28',
    image:
      'https://images.unsplash.com/photo-1579783902614-a3fb3927b6a5?auto=format&fit=crop&w=1000&q=85',
    alt: '美術館展廳中的古典畫作',
    tone: 'olive',
  },
  {
    category: '特別企劃',
    title: '日常收藏家',
    subtitle: '那些被好好珍藏的平凡片刻',
    date: '2025.07.19 — 2025.11.02',
    image:
      'https://images.unsplash.com/photo-1578301978693-85fa9c0320b9?auto=format&fit=crop&w=1000&q=85',
    alt: '展覽空間裡的現代藝術作品',
    tone: 'blue',
  },
]

const news = [
  { date: '2025.06.20', tag: '活動公告', title: '夏日夜間開館｜週五延長開放至晚間九點' },
  { date: '2025.06.12', tag: '教育推廣', title: '親子藝術工作坊：把一片風景帶回家' },
  { date: '2025.06.05', tag: '最新消息', title: '本館典藏數位資料庫全新改版上線' },
]
</script>

<template>
  <div class="museum-site">
    <div class="announcement">
      <span class="announcement-label">本週公告</span>
      <p>端午連假期間正常開館，週一休館日順延至 6 月 2 日</p>
      <a href="#visit" aria-label="查看參觀資訊">參觀須知 <span>↗</span></a>
    </div>

    <header class="site-header">
      <a class="brand" href="#top" aria-label="市立美術館首頁" @click="menuOpen = false">
        <span class="brand-mark" aria-hidden="true"><span></span><span></span><span></span></span>
        <span class="brand-copy">
          <strong>市立美術館</strong>
          <small>THE CITY ART MUSEUM</small>
        </span>
      </a>

      <button
        class="menu-toggle"
        type="button"
        :aria-expanded="menuOpen"
        aria-label="切換導覽選單"
        @click="menuOpen = !menuOpen"
      >
        <span></span><span></span>
      </button>

      <nav class="main-nav" :class="{ 'is-open': menuOpen }" aria-label="主要導覽">
        <a href="#exhibitions" @click="menuOpen = false">展覽活動</a>
        <a href="#news" @click="menuOpen = false">最新消息</a>
        <RouterLink to="/cross-museum-guide" @click="menuOpen = false">跨館 AI 導覽</RouterLink>
        <a href="#about" @click="menuOpen = false">認識美術館</a>
        <a href="#visit" @click="menuOpen = false">參觀資訊</a>
        <a class="nav-ticket" href="#visit" @click="menuOpen = false">
          規劃參觀 <span aria-hidden="true">↗</span>
        </a>
      </nav>
    </header>

    <main id="top">
      <section class="hero" aria-labelledby="hero-title">
        <img
          class="hero-image"
          src="https://images.unsplash.com/photo-1577083552431-6e5fd01aa342?auto=format&fit=crop&w=2200&q=90"
          alt=""
        />
        <div class="hero-shade"></div>
        <div class="hero-content">
          <p class="eyebrow"><span></span> 一座讓日常遇見藝術的美術館</p>
          <h1 id="hero-title">在藝術裡，<br />看見生活的<span>另一種可能。</span></h1>
          <p class="hero-description">
            收藏城市的故事，也收藏每一次觀看的感動。<br class="desktop-break" />
            邀請你走進美術館，與藝術相遇。
          </p>
          <a class="button button-light" href="#exhibitions">
            探索現在的展覽 <span aria-hidden="true">↗</span>
          </a>
        </div>
        <div class="hero-index"><span>01</span><i></i> 03</div>
        <div class="hero-caption">光的形狀・展覽現場</div>
      </section>

      <section class="quick-info" aria-label="今日開館資訊">
        <div class="quick-open">
          <span class="open-indicator"></span>
          <div><strong>今日開館中</strong><small>週二至週日 09:30 — 17:30</small></div>
        </div>
        <a href="#exhibitions" class="quick-item">
          <span class="quick-number">03</span>
          <span><strong>檔精彩展覽</strong><small>探索當期展覽</small></span>
          <b aria-hidden="true">↗</b>
        </a>
        <a href="#visit" class="quick-item">
          <span class="quick-icon" aria-hidden="true">⌖</span>
          <span><strong>計畫你的旅程</strong><small>交通・票價・開放時間</small></span>
          <b aria-hidden="true">↗</b>
        </a>
        <a href="#news" class="quick-item">
          <span class="quick-icon" aria-hidden="true">✳</span>
          <span><strong>美術館大小事</strong><small>活動與最新消息</small></span>
          <b aria-hidden="true">↗</b>
        </a>
      </section>

      <section id="exhibitions" class="section exhibitions-section">
        <div class="section-heading">
          <div>
            <p class="eyebrow eyebrow-dark">WHAT'S ON</p>
            <h2>此刻，正在發生的<span>美好。</span></h2>
            <p class="section-intro">每一次走進展場，都是一次新的相遇。</p>
          </div>
          <a class="text-link" href="#visit">所有展覽與活動 <span aria-hidden="true">↗</span></a>
        </div>

        <div class="exhibition-grid">
          <article
            v-for="(exhibition, index) in exhibitions"
            :key="exhibition.title"
            class="exhibition-card"
            :class="`tone-${exhibition.tone}`"
          >
            <a class="exhibition-image" href="#visit" :aria-label="`了解${exhibition.title}展覽`">
              <img :src="exhibition.image" :alt="exhibition.alt" loading="lazy" />
              <span class="card-index">0{{ index + 1 }}</span>
              <span class="image-arrow" aria-hidden="true">↗</span>
            </a>
            <div class="exhibition-details">
              <p class="card-category">{{ exhibition.category }} <span>・</span> 展覽中</p>
              <h3>{{ exhibition.title }}</h3>
              <p class="card-subtitle">{{ exhibition.subtitle }}</p>
              <p class="card-date">{{ exhibition.date }}</p>
            </div>
          </article>
        </div>
      </section>

      <section id="about" class="about-band">
        <div class="about-art" aria-hidden="true">
          <img
            src="https://images.unsplash.com/photo-1579783902614-a3fb3927b6a5?auto=format&fit=crop&w=1000&q=85"
            alt=""
            loading="lazy"
          />
          <span class="art-note">A PLACE TO<br />SLOW DOWN.</span>
        </div>
        <div class="about-copy">
          <p class="eyebrow">A MUSEUM FOR EVERYONE</p>
          <h2>藝術不只是<br />遠方的風景。</h2>
          <p>
            我們相信，藝術能讓城市更靠近彼此。從一件作品、一場對話開始，讓美術館成為每個人都能自在走進的地方。
          </p>
          <a class="button button-outline" href="#visit">認識我們 <span aria-hidden="true">↗</span></a>
        </div>
        <div class="about-stamp" aria-hidden="true">EST.<br /><strong>1983</strong></div>
      </section>

      <section id="news" class="section news-section">
        <div class="section-heading news-heading">
          <div>
            <p class="eyebrow eyebrow-dark">FROM THE MUSEUM</p>
            <h2>美術館<span>新鮮事</span></h2>
          </div>
          <a class="text-link" href="#news">閱讀所有消息 <span aria-hidden="true">↗</span></a>
        </div>
        <div class="news-list">
          <a v-for="item in news" :key="item.title" class="news-row" href="#visit">
            <time>{{ item.date }}</time>
            <span class="news-tag">{{ item.tag }}</span>
            <strong>{{ item.title }}</strong>
            <span class="news-arrow" aria-hidden="true">↗</span>
          </a>
        </div>
      </section>

      <section id="visit" class="visit-section">
        <div class="visit-copy">
          <p class="eyebrow">PLAN YOUR VISIT</p>
          <h2>今天，就來<br />美術館走走。</h2>
          <p>留一點時間給自己，讓藝術為今天帶來不一樣的風景。</p>
          <a class="button button-light" href="https://maps.google.com/?q=台北市立美術館" target="_blank" rel="noreferrer">
            開始規劃行程 <span aria-hidden="true">↗</span>
          </a>
        </div>
        <div class="visit-details">
          <div class="visit-detail">
            <span class="detail-icon" aria-hidden="true">◷</span>
            <div><small>開放時間</small><strong>週二至週日 09:30 — 17:30</strong><p>週六延長開放至 20:30・週一休館</p></div>
          </div>
          <div class="visit-detail">
            <span class="detail-icon" aria-hidden="true">⌖</span>
            <div><small>美術館地址</small><strong>台北市中山區中山北路三段 181 號</strong><p>捷運圓山站 1 號出口，步行約 5 分鐘</p></div>
          </div>
          <div class="visit-detail">
            <span class="detail-icon" aria-hidden="true">＄</span>
            <div><small>參觀票價</small><strong>全票 NT$ 30・優待票 NT$ 15</strong><p>未滿 18 歲及本市市民免費入館</p></div>
          </div>
        </div>
      </section>
    </main>

    <footer class="site-footer">
      <div class="footer-main">
        <a class="brand footer-brand" href="#top" aria-label="市立美術館首頁">
          <span class="brand-mark" aria-hidden="true"><span></span><span></span><span></span></span>
          <span class="brand-copy"><strong>市立美術館</strong><small>THE CITY ART MUSEUM</small></span>
        </a>
        <p>讓藝術，成為生活的一部分。</p>
        <div class="footer-links"><a href="#about">關於美術館</a><a href="#visit">聯絡我們</a><a href="#visit">交通資訊</a></div>
      </div>
      <div class="footer-bottom">
        <span>© 2025 市立美術館・本網站內容為模擬展示</span>
        <a href="#top">BACK TO TOP ↑</a>
      </div>
    </footer>
  </div>
</template>

<style scoped>
.museum-site {
  overflow: hidden;
  background: #f8f7f3;
}

.announcement {
  min-height: 36px;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 13px;
  padding: 5px 24px;
  color: #fff;
  background: #34372d;
  font-size: 11px;
  letter-spacing: 0.04em;
}

.announcement-label {
  color: #e7cba5;
  font-weight: 700;
}

.announcement a {
  margin-left: 10px;
  color: #e7cba5;
}

.site-header {
  height: 82px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 max(calc((100vw - 1280px) / 2), 6.5%);
  background: #f8f7f3;
  position: relative;
  z-index: 5;
}

.brand {
  display: flex;
  align-items: center;
  gap: 11px;
}

.brand-mark {
  width: 34px;
  height: 34px;
  display: flex;
  align-items: flex-end;
  gap: 3px;
  padding: 5px;
  border: 1px solid #b74734;
  transform: rotate(-7deg);
}

.brand-mark span {
  width: 6px;
  background: #b74734;
}

.brand-mark span:nth-child(1) { height: 14px; }
.brand-mark span:nth-child(2) { height: 21px; }
.brand-mark span:nth-child(3) { height: 11px; }

.brand-copy {
  display: flex;
  flex-direction: column;
  line-height: 1.2;
}

.brand-copy strong {
  font-size: 16px;
  letter-spacing: 0.14em;
  font-weight: 700;
}

.brand-copy small {
  margin-top: 4px;
  color: #8b877e;
  font-family: Arial, sans-serif;
  font-size: 8px;
  letter-spacing: 0.12em;
}

.main-nav {
  display: flex;
  align-items: center;
  gap: 37px;
  font-size: 12px;
  letter-spacing: 0.06em;
}

.main-nav > a:not(.nav-ticket):hover,
.footer-links a:hover,
.text-link:hover {
  color: #b74734;
}

.main-nav .nav-ticket {
  padding: 11px 17px;
  border: 1px solid #b74734;
  color: #a83e2e;
  transition: color 0.2s, background 0.2s;
}

.nav-ticket:hover {
  color: #fff;
  background: #b74734;
}

.nav-ticket span { margin-left: 8px; }
.menu-toggle { display: none; }

.hero {
  height: min(640px, 57vw);
  min-height: 490px;
  position: relative;
  display: flex;
  align-items: center;
  color: #fff;
  background: #35332e;
}

.hero-image,
.hero-shade {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
}

.hero-image {
  object-fit: cover;
  object-position: center 47%;
  opacity: 0.78;
}

.hero-shade {
  background: linear-gradient(90deg, rgba(29, 30, 26, 0.82) 0%, rgba(29, 30, 26, 0.53) 43%, rgba(29, 30, 26, 0.04) 100%),
    linear-gradient(0deg, rgba(24, 24, 20, 0.24), transparent 38%);
}

.hero-content {
  width: min(1280px, 87%);
  margin: 4px auto 0;
  position: relative;
  z-index: 1;
}

.eyebrow {
  display: flex;
  align-items: center;
  gap: 10px;
  color: #d3b992;
  font-family: Arial, sans-serif;
  font-size: 10px;
  font-weight: 600;
  letter-spacing: 0.17em;
}

.eyebrow > span {
  width: 23px;
  height: 1px;
  background: #d3b992;
}

.hero h1 {
  margin-top: 22px;
  font-size: clamp(42px, 5.2vw, 72px);
  font-weight: 500;
  letter-spacing: 0.035em;
  line-height: 1.36;
}

.hero h1 span { color: #ebc99e; }

.hero-description {
  margin-top: 17px;
  color: rgba(255, 255, 255, 0.78);
  font-size: 13px;
  line-height: 2;
  letter-spacing: 0.04em;
}

.button {
  min-height: 48px;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 35px;
  padding: 0 20px;
  font-size: 11px;
  letter-spacing: 0.08em;
  transition: background 0.2s, color 0.2s, border-color 0.2s;
}

.button-light {
  margin-top: 29px;
  color: #272721;
  background: #f1e7d7;
}

.button-light:hover { background: #fff; }

.hero-index {
  position: absolute;
  right: 6.5%;
  bottom: 34px;
  display: flex;
  align-items: center;
  gap: 10px;
  color: rgba(255, 255, 255, 0.64);
  font-family: Arial, sans-serif;
  font-size: 10px;
}

.hero-index span { color: #fff; }
.hero-index i { width: 34px; height: 1px; background: rgba(255, 255, 255, 0.6); }
.hero-caption { position: absolute; right: 6.5%; top: 50%; writing-mode: vertical-rl; font-size: 9px; letter-spacing: 0.16em; opacity: 0.8; }

.quick-info {
  min-height: 112px;
  display: grid;
  grid-template-columns: 1.1fr 1fr 1fr 1fr;
  align-items: center;
  padding: 0 max(calc((100vw - 1280px) / 2), 6.5%);
  background: #eeece5;
}

.quick-open,
.quick-item {
  min-height: 54px;
  display: flex;
  align-items: center;
}

.quick-open { gap: 12px; }
.open-indicator { width: 8px; height: 8px; border-radius: 50%; background: #6c8758; box-shadow: 0 0 0 4px #dce4d5; }
.quick-open div,
.quick-item > span:nth-child(2) { display: flex; flex-direction: column; }
.quick-open strong,
.quick-item strong { font-size: 12px; font-weight: 600; letter-spacing: 0.04em; }
.quick-open small,
.quick-item small { margin-top: 3px; color: #7c7971; font-size: 10px; }

.quick-item {
  gap: 13px;
  padding: 0 14px;
  border-left: 1px solid #d9d6cd;
}

.quick-number { color: #b74734; font-family: Georgia, serif; font-size: 34px; line-height: 1; }
.quick-icon { width: 35px; color: #a44836; font-size: 25px; text-align: center; }
.quick-item > b { margin-left: auto; color: #a44836; font-size: 15px; font-weight: 400; transition: transform 0.2s; }
.quick-item:hover > b { transform: translate(3px, -3px); }

.section {
  width: min(1280px, 87%);
  margin: 0 auto;
}

.exhibitions-section { padding-top: 99px; padding-bottom: 108px; }

.section-heading {
  display: flex;
  align-items: flex-end;
  justify-content: space-between;
  margin-bottom: 35px;
}

.eyebrow-dark { color: #9e4535; }

.section-heading h2 {
  margin-top: 12px;
  font-size: clamp(28px, 3vw, 38px);
  font-weight: 500;
  letter-spacing: 0.06em;
}

.section-heading h2 span { color: #b74734; }
.section-intro { margin-top: 8px; color: #77746d; font-size: 12px; letter-spacing: 0.04em; }

.text-link {
  display: inline-flex;
  align-items: center;
  gap: 22px;
  margin-bottom: 5px;
  padding-bottom: 8px;
  border-bottom: 1px solid #b7b2a7;
  font-size: 11px;
  letter-spacing: 0.06em;
  transition: color 0.2s;
}

.text-link span { color: #b74734; }
.exhibition-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 25px; }
.exhibition-card { min-width: 0; }

.exhibition-image {
  height: 300px;
  display: block;
  position: relative;
  overflow: hidden;
  background: #dedbd2;
}

.exhibition-image::after { content: ''; position: absolute; inset: 40% 0 0; background: linear-gradient(0deg, rgba(26, 25, 22, 0.36), transparent); }
.exhibition-image img { width: 100%; height: 100%; display: block; object-fit: cover; transition: transform 0.6s cubic-bezier(0.2, 0.7, 0.2, 1); }
.exhibition-card:hover .exhibition-image img { transform: scale(1.045); }
.card-index { position: absolute; z-index: 1; top: 15px; left: 16px; color: #fff; font-family: Georgia, serif; font-size: 12px; }
.image-arrow { width: 36px; height: 36px; position: absolute; z-index: 1; right: 15px; bottom: 15px; display: grid; place-items: center; border: 1px solid rgba(255, 255, 255, 0.8); border-radius: 50%; color: #fff; transition: color 0.2s, background 0.2s; }
.exhibition-card:hover .image-arrow { color: #333; background: #fff; }
.exhibition-details { padding: 19px 2px 0; }
.card-category { color: #a84b3a; font-size: 10px; letter-spacing: 0.09em; }
.card-category span { margin: 0 4px; color: #aca69a; }
.exhibition-details h3 { margin-top: 7px; font-size: 23px; font-weight: 500; letter-spacing: 0.07em; }
.card-subtitle { margin-top: 3px; color: #77746d; font-size: 11px; }
.card-date { margin-top: 16px; padding-top: 11px; border-top: 1px solid #e1ded5; color: #858178; font-family: Arial, sans-serif; font-size: 10px; letter-spacing: 0.06em; }

.about-band {
  min-height: 435px;
  display: grid;
  grid-template-columns: 1.08fr 0.92fr;
  position: relative;
  color: #fff;
  background: #414338;
}

.about-art { min-height: 435px; position: relative; overflow: hidden; }
.about-art::after { content: ''; position: absolute; inset: 0; background: linear-gradient(90deg, transparent 65%, #414338 100%), linear-gradient(0deg, rgba(28, 28, 25, 0.17), transparent); }
.about-art img { width: 100%; height: 100%; position: absolute; inset: 0; object-fit: cover; object-position: center 45%; opacity: 0.8; }
.art-note { position: absolute; z-index: 1; bottom: 32px; left: 8%; color: rgba(255, 255, 255, 0.83); font-family: Arial, sans-serif; font-size: 10px; letter-spacing: 0.2em; line-height: 1.8; }
.about-copy { max-width: 510px; align-self: center; padding: 58px 14% 58px 9%; }
.about-copy h2 { margin-top: 17px; font-size: 43px; font-weight: 400; letter-spacing: 0.08em; line-height: 1.5; }
.about-copy > p:not(.eyebrow) { max-width: 370px; margin-top: 14px; color: #d0cfc6; font-size: 12px; line-height: 2.1; letter-spacing: 0.03em; }
.button-outline { margin-top: 22px; border: 1px solid rgba(255, 255, 255, 0.56); color: #fff; }
.button-outline:hover { color: #34372d; background: #fff; }
.about-stamp { position: absolute; right: 6.5%; bottom: 27px; color: #d4c6a8; font-family: Arial, sans-serif; font-size: 8px; letter-spacing: 0.16em; line-height: 1.5; text-align: center; }
.about-stamp strong { font-size: 16px; font-weight: 400; }

.news-section { padding-top: 92px; padding-bottom: 100px; }
.news-heading { align-items: flex-end; margin-bottom: 25px; }
.news-list { border-top: 1px solid #dcd9d0; }
.news-row { min-height: 68px; display: grid; grid-template-columns: 130px 100px 1fr 20px; align-items: center; gap: 17px; border-bottom: 1px solid #dcd9d0; transition: padding 0.2s, color 0.2s; }
.news-row:hover { padding-right: 5px; padding-left: 5px; color: #a84736; }
.news-row time { color: #827e74; font-family: Arial, sans-serif; font-size: 10px; letter-spacing: 0.05em; }
.news-tag { width: fit-content; padding: 3px 9px; border: 1px solid #d9d3c7; color: #79756c; font-size: 9px; letter-spacing: 0.04em; }
.news-row strong { font-size: 12px; font-weight: 500; letter-spacing: 0.03em; }
.news-arrow { justify-self: end; color: #a84736; }

.visit-section {
  min-height: 383px;
  display: grid;
  grid-template-columns: 0.95fr 1.05fr;
  padding: 70px max(calc((100vw - 1280px) / 2), 6.5%);
  color: #fff;
  background: #ad4937;
}

.visit-copy { padding-right: 13%; border-right: 1px solid rgba(255, 255, 255, 0.25); }
.visit-copy .eyebrow { color: #eed3b1; }
.visit-copy h2 { margin-top: 15px; font-size: 38px; font-weight: 400; letter-spacing: 0.08em; line-height: 1.45; }
.visit-copy > p:not(.eyebrow) { margin-top: 10px; color: rgba(255, 255, 255, 0.75); font-size: 11px; letter-spacing: 0.04em; }
.visit-copy .button { margin-top: 20px; }
.visit-details { display: flex; flex-direction: column; justify-content: center; gap: 22px; padding-left: 13%; }
.visit-detail { display: flex; align-items: flex-start; gap: 14px; }
.detail-icon { width: 30px; color: #edd0ad; font-size: 20px; text-align: center; }
.visit-detail div { display: flex; flex-direction: column; }
.visit-detail small { color: #eed3b1; font-size: 9px; letter-spacing: 0.12em; }
.visit-detail strong { margin-top: 4px; font-size: 12px; font-weight: 500; letter-spacing: 0.04em; }
.visit-detail p { margin-top: 2px; color: rgba(255, 255, 255, 0.7); font-size: 10px; }

.site-footer { padding: 38px max(calc((100vw - 1280px) / 2), 6.5%) 0; background: #eeece5; }
.footer-main { min-height: 86px; display: flex; align-items: center; justify-content: space-between; }
.footer-brand .brand-mark { width: 30px; height: 30px; }
.footer-brand .brand-copy strong { font-size: 14px; }
.footer-main > p { color: #77746d; font-size: 11px; letter-spacing: 0.1em; }
.footer-links { display: flex; gap: 25px; color: #6f6c64; font-size: 10px; }
.footer-links a { transition: color 0.2s; }
.footer-bottom { min-height: 42px; display: flex; align-items: center; justify-content: space-between; border-top: 1px solid #d8d5cc; color: #8a867d; font-family: Arial, sans-serif; font-size: 9px; letter-spacing: 0.07em; }
.footer-bottom a { color: #58564f; }

@media (max-width: 900px) {
  .site-header { padding-right: 5%; padding-left: 5%; }
  .main-nav { gap: 19px; }
  .hero-content,
  .section { width: 90%; }
  .quick-info { padding-right: 5%; padding-left: 5%; }
  .quick-item { gap: 8px; padding-right: 8px; padding-left: 10px; }
  .quick-item small { font-size: 9px; }
  .exhibition-grid { gap: 16px; }
  .exhibition-image { height: 240px; }
  .visit-section { padding-right: 5%; padding-left: 5%; }
  .site-footer { padding-right: 5%; padding-left: 5%; }
}

@media (max-width: 650px) {
  .announcement { justify-content: flex-start; gap: 8px; padding-right: 12px; padding-left: 12px; font-size: 9px; }
  .announcement-label { flex-shrink: 0; }
  .announcement p { overflow: hidden; text-overflow: ellipsis; white-space: nowrap; }
  .announcement a { flex-shrink: 0; margin-left: 0; }
  .site-header { height: 70px; padding: 0 6%; }
  .brand-mark { width: 31px; height: 31px; }
  .brand-copy strong { font-size: 14px; }
  .menu-toggle { width: 40px; height: 40px; display: flex; flex-direction: column; justify-content: center; gap: 6px; align-items: center; border: 1px solid #d8d3c9; background: transparent; }
  .menu-toggle span { width: 17px; height: 1px; background: #37362f; }
  .main-nav { position: absolute; top: 70px; right: 0; left: 0; display: none; align-items: stretch; gap: 0; padding: 8px 6% 20px; background: #f8f7f3; box-shadow: 0 12px 15px rgba(0, 0, 0, 0.08); }
  .main-nav.is-open { display: flex; flex-direction: column; }
  .main-nav > a:not(.nav-ticket) { padding: 13px 0; border-bottom: 1px solid #e4e1d9; }
  .main-nav .nav-ticket { margin-top: 13px; text-align: center; }
  .hero { height: 590px; min-height: 0; align-items: flex-end; padding-bottom: 70px; }
  .hero-image { object-position: 55% center; }
  .hero-shade { background: linear-gradient(0deg, rgba(25, 25, 22, 0.82), rgba(25, 25, 22, 0.18) 85%); }
  .hero-content { width: 88%; margin: 0 auto; }
  .hero h1 { margin-top: 17px; font-size: clamp(38px, 10vw, 51px); }
  .hero-description { font-size: 11px; }
  .button { min-height: 45px; }
  .hero-index { right: 6%; bottom: 20px; }
  .hero-caption { top: 20px; right: 6%; }
  .quick-info { grid-template-columns: 1fr 1fr; padding: 13px 6%; }
  .quick-open { min-height: 68px; padding-left: 5px; }
  .quick-item { min-height: 68px; padding: 0 7px; border-left: 1px solid #d9d6cd; }
  .quick-item:nth-child(3) { border-left: 0; border-top: 1px solid #d9d6cd; }
  .quick-item:nth-child(4) { border-top: 1px solid #d9d6cd; }
  .quick-number { font-size: 28px; }
  .quick-icon { width: 28px; font-size: 21px; }
  .quick-open strong, .quick-item strong { font-size: 10px; }
  .quick-open small, .quick-item small { font-size: 8px; }
  .exhibitions-section { padding-top: 67px; padding-bottom: 69px; }
  .section-heading { align-items: flex-start; gap: 18px; margin-bottom: 26px; }
  .section-heading h2 { font-size: 26px; }
  .section-intro { font-size: 10px; }
  .section-heading > .text-link { flex-shrink: 0; gap: 8px; margin-top: 25px; font-size: 9px; }
  .exhibition-grid { grid-template-columns: 1fr; gap: 32px; }
  .exhibition-image { height: 280px; }
  .exhibition-details { padding-top: 14px; }
  .exhibition-details h3 { font-size: 21px; }
  .card-date { margin-top: 11px; }
  .about-band { grid-template-columns: 1fr; }
  .about-art { min-height: 260px; }
  .about-art::after { background: linear-gradient(0deg, #414338 0%, transparent 45%); }
  .art-note { bottom: 18px; }
  .about-copy { padding: 8px 7% 56px; }
  .about-copy h2 { font-size: 36px; }
  .about-stamp { right: 7%; bottom: 22px; }
  .news-section { padding-top: 66px; padding-bottom: 72px; }
  .news-heading { align-items: flex-end; }
  .news-heading h2 { font-size: 28px; }
  .news-row { min-height: 77px; grid-template-columns: 82px 1fr 18px; gap: 7px 10px; padding: 9px 0; }
  .news-row time { grid-column: 1; grid-row: 1; font-size: 9px; }
  .news-tag { grid-column: 1; grid-row: 2; font-size: 8px; }
  .news-row strong { grid-column: 2; grid-row: 1 / span 2; font-size: 10px; line-height: 1.7; }
  .news-arrow { grid-column: 3; grid-row: 1 / span 2; }
  .visit-section { grid-template-columns: 1fr; padding: 52px 7%; }
  .visit-copy { padding: 0 0 30px; border-right: 0; border-bottom: 1px solid rgba(255, 255, 255, 0.25); }
  .visit-copy h2 { font-size: 34px; }
  .visit-details { gap: 20px; padding: 28px 0 0; }
  .visit-detail strong { font-size: 11px; }
  .visit-detail p { font-size: 9px; }
  .footer-main { align-items: flex-start; flex-wrap: wrap; gap: 17px; padding: 23px 0; }
  .footer-main > p { order: 3; width: 100%; }
  .footer-links { gap: 13px; font-size: 9px; }
  .footer-bottom { min-height: 48px; gap: 12px; font-size: 8px; }
}

@media (prefers-reduced-motion: reduce) {
  *,
  *::before,
  *::after {
    scroll-behavior: auto !important;
    transition-duration: 0.01ms !important;
  }
}
</style>
