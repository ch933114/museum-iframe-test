<script setup lang="ts">
import { RouterLink } from 'vue-router'
</script>

<template>
  <div class="guide-page">
    <header class="guide-header">
      <RouterLink class="brand" to="/" aria-label="返回市立美術館首頁">
        <span class="brand-mark" aria-hidden="true"><span></span><span></span><span></span></span>
        <span class="brand-copy">
          <strong>市立美術館</strong>
          <small>THE CITY ART MUSEUM</small>
        </span>
      </RouterLink>
      <nav aria-label="頁面導覽">
        <RouterLink class="back-link" to="/">返回首頁 <span aria-hidden="true">↗</span></RouterLink>
      </nav>
    </header>

    <main class="guide-main">
      <div class="guide-heading">
        <div>
          <p class="eyebrow">CROSS-MUSEUM AI GUIDE</p>
          <h1>跨館 AI 導覽員</h1>
          <p class="guide-description">探索不同場館的典藏與故事，開啟一段跨越博物館的藝文旅程。</p>
        </div>
        <span class="guide-label"><span></span> AI 導覽服務</span>
      </div>

      <section class="guide-frame-wrap" aria-label="跨館 AI 導覽服務">
        <iframe
          class="guide-frame"
          src="https://moeai-test.omniguider.com/home/nmns"
          title="跨館 AI 導覽員"
          allow="camera; microphone"
        ></iframe>
      </section>
    </main>

    <footer class="guide-footer">
      <span>市立美術館・跨館 AI 導覽服務</span>
      <RouterLink to="/">返回美術館首頁 ↑</RouterLink>
    </footer>
  </div>
</template>

<style scoped>
.guide-page {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  background: #f8f7f3;
}

.guide-header {
  height: 82px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 max(calc((100vw - 1280px) / 2), 6.5%);
  border-bottom: 1px solid #e5e2d9;
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
  font-weight: 700;
  letter-spacing: 0.14em;
}

.brand-copy small {
  margin-top: 4px;
  color: #8b877e;
  font-family: Arial, sans-serif;
  font-size: 8px;
  letter-spacing: 0.12em;
}

.back-link {
  color: #a84333;
  font-size: 11px;
  letter-spacing: 0.06em;
}

.back-link span {
  margin-left: 8px;
}

.guide-main {
  width: min(1280px, 87%);
  flex: 1;
  margin: 0 auto;
  padding: 39px 0 32px;
}

.guide-heading {
  display: flex;
  align-items: flex-end;
  justify-content: space-between;
  gap: 24px;
  margin-bottom: 23px;
}

.eyebrow {
  color: #9e4535;
  font-family: Arial, sans-serif;
  font-size: 10px;
  font-weight: 600;
  letter-spacing: 0.17em;
}

.guide-heading h1 {
  margin-top: 7px;
  font-size: clamp(26px, 3vw, 36px);
  font-weight: 500;
  letter-spacing: 0.08em;
}

.guide-description {
  margin-top: 6px;
  color: #77746d;
  font-size: 12px;
  letter-spacing: 0.03em;
}

.guide-label {
  display: inline-flex;
  align-items: center;
  gap: 9px;
  padding: 8px 12px;
  border: 1px solid #d9d6cd;
  color: #6b6a60;
  font-size: 10px;
  letter-spacing: 0.05em;
  white-space: nowrap;
}

.guide-label span {
  width: 7px;
  height: 7px;
  border-radius: 50%;
  background: #6c8758;
}

.guide-frame-wrap {
  height: clamp(560px, calc(100vh - 260px), 820px);
  display: flex;
  justify-content: center;
  overflow: hidden;
  container-type: size;
}

.guide-frame {
  width: min(100%, 56.25cqh);
  height: 100%;
  display: block;
  border: 0;
  background: transparent;
}

.guide-footer {
  min-height: 48px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 max(calc((100vw - 1280px) / 2), 6.5%);
  border-top: 1px solid #e1ded5;
  color: #858178;
  font-size: 9px;
  letter-spacing: 0.05em;
}

.guide-footer a {
  color: #a84333;
}

@media (max-width: 650px) {
  .guide-header {
    height: 70px;
    padding: 0 6%;
  }

  .brand-mark {
    width: 31px;
    height: 31px;
  }

  .brand-copy strong {
    font-size: 14px;
  }

  .guide-main {
    width: 90%;
    padding: 30px 0 22px;
  }

  .guide-heading {
    align-items: flex-start;
    flex-direction: column;
    gap: 13px;
    margin-bottom: 17px;
  }

  .guide-description {
    font-size: 11px;
    line-height: 1.8;
  }

  .guide-label {
    padding: 6px 9px;
  }

  .guide-frame-wrap {
    height: min(max(560px, calc(100dvh - 260px)), 160vw);
  }

  .guide-footer {
    padding: 0 5%;
    font-size: 8px;
  }
}
</style>
