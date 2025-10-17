<script setup lang="ts">
interface TraditionCard {
  title: string
  subtitle: string
  details: string
}

interface TimelineEvent {
  time: string
  activity: string
  note: string
}

const traditionCards: TraditionCard[] = [
  {
    title: '보름달 맞이 소원 빌기',
    subtitle: '환한 달빛 아래 드리는 감사',
    details:
      '가족이 둘러앉아 한 해를 무사히 보내게 해준 자연과 조상님께 마음을 전합니다. 달에게 속삭인 소원은 서로의 기도로 이어집니다.'
  },
  {
    title: '풍성한 송편 빚기',
    subtitle: '손끝에서 피어나는 온기',
    details:
      '쌀가루에 제철 재료를 넣어 반달 모양 송편을 빚습니다. 송편이 예쁘면 예쁜 딸이 생긴다는 말처럼 웃음소리가 부엌을 가득 채웁니다.'
  },
  {
    title: '친지와 이웃 나눔',
    subtitle: '함께할수록 커지는 기쁨',
    details:
      '정성스레 마련한 음식을 나누고 서로의 안부를 묻습니다. 타지에 있는 이들에게는 따뜻한 메시지로 마음을 전하며 정을 이어갑니다.'
  }
]

const timeline: TimelineEvent[] = [
  {
    time: '17:30',
    activity: '저녁 준비 & 차례상 꾸미기',
    note: '집안 구석구석 달맞이 장식과 촛불을 켜고, 정갈하게 차례상을 차립니다.'
  },
  {
    time: '19:00',
    activity: '보름달 아래 한마당',
    note: '달을 향해 절을 올리고 올 한 해의 감사와 앞으로의 안녕을 빕니다.'
  },
  {
    time: '20:30',
    activity: '담소와 풍류',
    note: '서로의 이야기를 들으며 송편과 과일을 나누고, 조용히 밤하늘을 올려다봅니다.'
  },
  {
    time: '22:00',
    activity: '달빛 산책',
    note: '달빛이 비추는 길을 천천히 걸어보며 올해의 행복한 순간들을 떠올립니다.'
  }
]

const wellWishes: string[] = [
  '가을 바람처럼 상쾌한 소식만 가득하길 바랄게요.',
  '멀리 있어도 마음은 늘 곁에 — 더 풍성한 한가위를 만나요.',
  '보름달처럼 둥근 웃음이 당신의 얼굴을 가득 채우길!',
  '함께한 그 시간들 덕분에 올 한 해도 든든했어요. 고맙습니다.',
  '밝은 달빛에 소원이 닿듯, 당신의 소망도 모두 이뤄지길.'
]

const lanterns = Array.from({ length: 6 }, (_, index) => index)

const lanternStyle = (index: number) => {
  const delay = index * 1.1
  const left = 8 + index * 15
  const duration = 12 + index * 2
  return {
    animationDelay: `${delay}s`,
    animationDuration: `${duration}s`,
    left: `${left}%`
  }
}
</script>

<template>
  <main class="page">
    <section class="sky">
      <div class="moon"></div>
      <ul class="lanterns">
        <li
          v-for="lantern in lanterns"
          :key="lantern"
          class="lantern"
          :style="lanternStyle(lantern)"
        >
          <span class="lantern-glow"></span>
        </li>
      </ul>
      <div class="hero">
        <p class="eyebrow">추석 · 한가위</p>
        <h1>풍요로운 보름달 아래, 마음 가득한 밤</h1>
        <p class="lead">
          가족과 이웃이 모여 한 해의 수확에 감사하고 서로의 기원을 나누는 한가위 밤입니다.
          코끝을 스치는 송편 향기와 환한 달빛이 당신의 마음도 포근히 비추길 바라요.
        </p>
        <a href="#traditions" class="pill">한가위 이야기에 흠뻑 빠져보기</a>
      </div>
    </section>

    <section id="traditions" class="content-section">
      <div class="section-heading">
        <h2>Harvest Moon Moments</h2>
        <p>조상님의 은혜에 감사하고 현재의 우리를 더 단단하게 만드는 세 가지 작은 의식들.</p>
      </div>
      <div class="cards">
        <article v-for="item in traditionCards" :key="item.title" class="card">
          <h3>{{ item.title }}</h3>
          <p class="subtitle">{{ item.subtitle }}</p>
          <p>{{ item.details }}</p>
        </article>
      </div>
    </section>

    <section class="timeline-section">
      <div class="section-heading">
        <h2>달빛 아래 일정표</h2>
        <p>보름달이 하늘 높이 떠오르는 순서대로 느긋하게 즐겨보세요.</p>
      </div>
      <ul class="timeline">
        <li v-for="slot in timeline" :key="slot.time" class="timeline-item">
          <span class="time">{{ slot.time }}</span>
          <div class="detail">
            <h3>{{ slot.activity }}</h3>
            <p>{{ slot.note }}</p>
          </div>
        </li>
      </ul>
    </section>

    <section class="wishes-section">
      <div class="section-heading">
        <h2>함께 나누는 마음</h2>
        <p>주고받는 안부 속에 더욱 환해지는 우리의 한가위.</p>
      </div>
      <ul class="wishes">
        <li v-for="wish in wellWishes" :key="wish" class="wish">{{ wish }}</li>
      </ul>
    </section>

    <footer class="footer">
      <small>가을 하늘의 달빛처럼 당신의 하루도 고요히 빛나길 — 즐거운 한가위 되세요!</small>
    </footer>
  </main>
</template>

<style scoped>
.page {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  background: radial-gradient(circle at top, #271b5a 0%, #0a0824 50%, #04030f 100%);
  color: #f8f6ff;
  font-family: 'Noto Sans KR', 'Segoe UI', system-ui, -apple-system, sans-serif;
  padding-bottom: 4rem;
}

.sky {
  position: relative;
  padding: 5rem 1.75rem 8rem;
  text-align: center;
  overflow: hidden;
}

.sky::before {
  content: '';
  position: absolute;
  inset: 0;
  background-image: radial-gradient(2px 2px at 20% 18%, rgba(255, 255, 255, 0.6) 0, transparent 60%),
    radial-gradient(1px 1px at 70% 12%, rgba(255, 255, 255, 0.35) 0, transparent 55%),
    radial-gradient(1px 1px at 35% 65%, rgba(255, 255, 255, 0.45) 0, transparent 55%),
    radial-gradient(2px 2px at 90% 80%, rgba(255, 255, 255, 0.35) 0, transparent 60%),
    radial-gradient(1px 1px at 55% 40%, rgba(255, 255, 255, 0.5) 0, transparent 55%);
  opacity: 0.75;
  animation: twinkle 12s linear infinite;
}

.moon {
  position: absolute;
  top: 12%;
  left: 50%;
  transform: translateX(-50%);
  width: 14rem;
  height: 14rem;
  background: radial-gradient(circle at 30% 30%, #fff8dc 0%, #f7e49a 55%, #d7b885 78%, #7f5b43 100%);
  border-radius: 50%;
  box-shadow: 0 0 120px rgba(255, 232, 150, 0.8), 0 0 240px rgba(255, 247, 209, 0.45);
  filter: drop-shadow(0 35px 55px rgba(126, 102, 255, 0.3));
  animation: moonGlow 10s ease-in-out infinite;
}

.lanterns {
  list-style: none;
  margin: 0;
  padding: 0;
  position: absolute;
  inset: 0;
  pointer-events: none;
}

.lantern {
  position: absolute;
  bottom: -4rem;
  width: 2.85rem;
  height: 3.5rem;
  background: linear-gradient(180deg, rgba(255, 180, 80, 0.8), rgba(255, 115, 115, 0.6));
  border-radius: 1.4rem 1.4rem 1rem 1rem;
  box-shadow: 0 0 12px rgba(255, 170, 100, 0.55);
  animation-name: floatLantern;
  animation-timing-function: ease-in;
  animation-iteration-count: infinite;
}

.lantern::after {
  content: '';
  position: absolute;
  bottom: -0.65rem;
  left: 50%;
  width: 0.6rem;
  height: 0.6rem;
  transform: translateX(-50%);
  border-radius: 50%;
  background: rgba(255, 214, 133, 0.9);
  box-shadow: 0 0 6px rgba(255, 218, 160, 0.8);
}

.lantern-glow {
  position: absolute;
  inset: 0;
  border-radius: inherit;
  background: radial-gradient(circle, rgba(255, 236, 188, 0.5) 0%, transparent 70%);
  opacity: 0.6;
  animation: lanternGlow 3.8s ease-in-out infinite;
}

.hero {
  position: relative;
  max-width: 42rem;
  margin: 0 auto;
  padding-top: 4rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
}

.eyebrow {
  font-size: 0.95rem;
  letter-spacing: 0.38rem;
  text-transform: uppercase;
  margin-bottom: 1.25rem;
  color: rgba(255, 217, 160, 0.85);
}

h1 {
  font-size: clamp(2.5rem, 6vw, 3.75rem);
  font-weight: 700;
  margin-bottom: 1.5rem;
  line-height: 1.15;
  text-shadow: 0 4px 28px rgba(40, 25, 95, 0.3);
}

.lead {
  font-size: 1.05rem;
  line-height: 1.7;
  margin-bottom: 2.5rem;
  color: rgba(231, 225, 255, 0.82);
}

.pill {
  display: inline-flex;
  padding: 0.85rem 2.4rem;
  border-radius: 999px;
  background: linear-gradient(135deg, #ffb56b 0%, #ff7c9a 100%);
  color: #1f143d;
  font-weight: 600;
  text-decoration: none;
  box-shadow: 0 12px 30px rgba(255, 158, 144, 0.35);
  transition: transform 180ms ease, box-shadow 180ms ease;
  align-self: center;
}

.pill:hover {
  transform: translateY(-3px);
  box-shadow: 0 16px 34px rgba(255, 170, 125, 0.45);
}

.content-section,
.timeline-section,
.wishes-section {
  padding: 0 1.75rem 5rem;
}

.section-heading {
  max-width: 640px;
  margin: 0 auto 2.5rem;
  text-align: center;
}

.section-heading h2 {
  font-size: clamp(1.8rem, 4vw, 2.6rem);
  margin-bottom: 1rem;
}

.section-heading p {
  color: rgba(220, 214, 255, 0.78);
  line-height: 1.6;
}

.cards {
  display: grid;
  gap: 1.75rem;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
}

.card {
  background: linear-gradient(160deg, rgba(29, 23, 73, 0.85), rgba(19, 15, 54, 0.8));
  border: 1px solid rgba(126, 102, 255, 0.2);
  border-radius: 1.4rem;
  padding: 2.25rem 1.85rem;
  box-shadow: 0 24px 40px -20px rgba(8, 5, 35, 0.8);
  backdrop-filter: blur(6px);
  text-align: left;
}

.card h3 {
  font-size: 1.35rem;
  margin-bottom: 0.8rem;
}

.subtitle {
  color: rgba(255, 214, 165, 0.85);
  margin-bottom: 0.95rem;
  font-weight: 600;
}

.card p {
  color: rgba(234, 230, 255, 0.82);
  line-height: 1.7;
}

.timeline {
  list-style: none;
  margin: 0;
  padding: 0;
  display: grid;
  gap: 1.5rem;
}

.timeline-item {
  display: grid;
  grid-template-columns: minmax(5rem, 7rem) 1fr;
  gap: 1.5rem;
  align-items: start;
  padding: 1.75rem 1.5rem;
  background: linear-gradient(135deg, rgba(21, 16, 55, 0.75), rgba(12, 9, 40, 0.9));
  border-radius: 1.35rem;
  border: 1px solid rgba(101, 84, 214, 0.25);
  box-shadow: 0 18px 32px -18px rgba(6, 4, 24, 0.85);
}

.time {
  font-weight: 700;
  color: rgba(255, 214, 165, 0.9);
  font-size: 1.1rem;
}

.detail h3 {
  margin: 0 0 0.6rem;
  font-size: 1.2rem;
}

.detail p {
  margin: 0;
  color: rgba(231, 227, 255, 0.8);
  line-height: 1.6;
}

.wishes {
  list-style: none;
  margin: 0;
  padding: 0;
  display: grid;
  gap: 1.2rem;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
}

.wish {
  border-radius: 999px;
  padding: 0.95rem 1.5rem;
  background: linear-gradient(120deg, rgba(32, 25, 70, 0.85), rgba(45, 30, 100, 0.85));
  border: 1px solid rgba(144, 120, 255, 0.18);
  color: rgba(226, 219, 255, 0.88);
  box-shadow: 0 16px 32px -24px rgba(0, 0, 0, 0.9);
  backdrop-filter: blur(6px);
}

.footer {
  text-align: center;
  margin-top: 3rem;
  padding: 0 1.75rem;
  color: rgba(205, 198, 255, 0.6);
  font-size: 0.9rem;
}

@keyframes twinkle {
  0%,
  100% {
    opacity: 0.65;
  }
  50% {
    opacity: 0.85;
  }
}

@keyframes moonGlow {
  0%,
  100% {
    transform: translateX(-50%) scale(1);
  }
  50% {
    transform: translateX(-50%) scale(1.04);
  }
}

@keyframes lanternGlow {
  0%,
  100% {
    opacity: 0.65;
  }
  50% {
    opacity: 0.9;
  }
}

@keyframes floatLantern {
  0% {
    transform: translateY(0);
    opacity: 0;
  }
  10% {
    opacity: 1;
  }
  100% {
    transform: translateY(-110vh);
    opacity: 0;
  }
}

@media (min-width: 768px) {
  .sky {
    padding: 6rem 3rem 9rem;
  }

  .hero {
    text-align: left;
    align-items: flex-start;
    padding-top: 6rem;
  }

  .lead {
    max-width: 36rem;
  }

  .content-section,
  .timeline-section,
  .wishes-section {
    padding: 0 3rem 6rem;
  }
}
</style>
