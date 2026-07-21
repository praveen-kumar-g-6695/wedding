<template>
  <div class="app-container" ref="scrollContainer" :style="{ '--font-scale': 1.2 }">
    <!-- PAGE 1: Invitation & Verses -->
    <div class="invite-card-wrapper" id="page-1">
      <div class="invite-card page-1-bg">
        <div class="kural-container">
          <Transition name="kural-fade" mode="out-in">
            <!-- Tamil Verse Stage -->
            <div v-if="currentStage === 'tamil'" key="tamil" class="verse-wrapper">
              <p class="kural-tamil">
                அன்பும் அறனும் உடைத்தாயின் இல்வாழ்க்கை<br>பண்பும் பயனும் அது.
              </p>
            </div>

            <!-- English Verse Stage -->
            <div v-else-if="currentStage === 'english'" key="english" class="verse-wrapper">
              <p class="kural-english">
                "Where love and virtue guide the way,<br>marriage finds its true purpose."
              </p>
            </div>

            <!-- Final Invitation Stage (Stays Permanently) -->
            <div v-else-if="currentStage === 'invite'" key="invite" class="verse-wrapper invite-wrapper">
              <p class="invite-sub">Together with our families</p>
              <h1 class="invite-names">
                Praveen Kumar G <span class="ampersand">&amp;</span> Vishnupriya R
              </h1>
              <p class="invite-text">
                we are so happy to invite you to share the joy and happiness of our wedding day
              </p>
            </div>
          </Transition>
        </div>

        <!-- Scroll down prompt for Page 2 -->
        <button v-if="currentStage === 'invite'" class="next-page-btn" @click="scrollToSecondPage">
          <span>Event Details</span>
          <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5">
            <path d="M12 5v14M19 12l-7 7-7-7"/>
          </svg>
        </button>
      </div>
    </div>

    <!-- PAGE 2: Event Dates & Timings -->
    <div class="invite-card-wrapper" id="page-2">
      <div class="invite-card page-2-bg">
        <div class="events-container">
          <h2 class="events-heading" :class="{ 'event-header-anim': showPage2Events }">
            Events &amp; Timings
          </h2>
          
          <!-- Reception -->
          <div class="event-block" :class="{ 'event-block-1-anim': showPage2Events }">
            <h3 class="event-title">RECEPTION</h3>
            <p class="event-date">Saturday, 22nd August 2026</p>
            <p class="event-time">7:00 PM Onwards</p>
          </div>

          <!-- Divider -->
          <div class="event-divider" :class="{ 'event-divider-anim': showPage2Events }">
            <svg width="60" height="10" viewBox="0 0 60 10" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path d="M0 5H22M38 5H60M30 2C31.6569 2 33 3.34315 33 5C33 6.65685 31.6569 8 30 8C28.3431 8 27 6.65685 27 5C27 3.34315 28.3431 2 30 2Z" stroke="#ba8d43" stroke-width="1.2" fill="#ba8d43"/>
            </svg>
          </div>

          <!-- Muhurtham -->
          <div class="event-block" :class="{ 'event-block-2-anim': showPage2Events }">
            <h3 class="event-title">MUHURTHAM</h3>
            <p class="event-date">Sunday, 23rd August 2026</p>
            <p class="event-time">7:30 AM – 9:00 AM</p>
          </div>
        </div>

        <!-- Back to Page 1 Button -->
        <button class="prev-page-btn" @click="scrollToFirstPage">
          <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5">
            <path d="M12 19V5M5 12l7-7 7 7"/>
          </svg>
          <span>Back</span>
        </button>

        <!-- Go to Page 3 Button -->
        <button class="next-page-btn" @click="scrollToThirdPage">
          <span>Venue &amp; Countdown</span>
          <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5">
            <path d="M12 5v14M19 12l-7 7-7-7"/>
          </svg>
        </button>
      </div>
    </div>

    <!-- PAGE 3: Venue Details & Countdown -->
    <div class="invite-card-wrapper" id="page-3">
      <div class="invite-card page-3-bg">
        <!-- Main Frame: Venue Info -->
        <div class="venue-container" :class="{ 'page3-venue-anim': showPage3Events }">
          <h2 class="venue-heading">VENUE</h2>
          <h1 class="venue-title">SRI SAKTHI THIRUMANA MAHAL</h1>
          
          <a href="https://maps.app.goo.gl/SNRaGRSrcdTCCfnB8" target="_blank" rel="noopener noreferrer" class="map-btn">
            <svg width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2">
              <path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z"/>
              <circle cx="12" cy="10" r="3"/>
            </svg>
            <span>View Location on Map</span>
          </a>
        </div>

        <!-- 3 Interlocked Circles: Countdown Timer -->
        <div class="timer-circle timer-circle-days" :class="{ 'page3-timer-anim': showPage3Events }">
          <span class="timer-val">{{ countdown.days }}</span>
          <span class="timer-label">DAYS</span>
        </div>

        <div class="timer-circle timer-circle-hours" :class="{ 'page3-timer-anim': showPage3Events }">
          <span class="timer-val">{{ countdown.hours }}</span>
          <span class="timer-label">HOURS</span>
        </div>

        <div class="timer-circle timer-circle-mins" :class="{ 'page3-timer-anim': showPage3Events }">
          <span class="timer-val">{{ countdown.minutes }}</span>
          <span class="timer-label">MINS</span>
        </div>

        <!-- Back to Page 2 Button -->
        <button class="prev-page-btn" @click="scrollToSecondPage">
          <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5">
            <path d="M12 19V5M5 12l7-7 7 7"/>
          </svg>
          <span>Back</span>
        </button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const scrollContainer = ref(null)
const currentStage = ref('initial')
const showPage2Events = ref(false)
const showPage3Events = ref(false)

const countdown = ref({ days: '00', hours: '00', minutes: '00' })
let timerInterval = null

function updateCountdown() {
  const targetDate = new Date('2026-08-23T07:30:00+05:30').getTime()
  const now = new Date().getTime()
  const diff = Math.max(0, targetDate - now)

  const days = Math.floor(diff / (1000 * 60 * 60 * 24))
  const hours = Math.floor((diff % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60))
  const minutes = Math.floor((diff % (1000 * 60 * 60)) / (1000 * 60))

  countdown.value = {
    days: String(days).padStart(2, '0'),
    hours: String(hours).padStart(2, '0'),
    minutes: String(minutes).padStart(2, '0')
  }
}

onMounted(() => {
  updateCountdown()
  timerInterval = setInterval(updateCountdown, 1000)

  // Step 1: At 1.0s, Tamil verse animates in
  setTimeout(() => {
    currentStage.value = 'tamil'
  }, 1000)

  // Step 2: At 5.5s, English verse animates in
  setTimeout(() => {
    currentStage.value = 'english'
  }, 5500)

  // Step 3: At 10.0s, Invitation text animates in (and stays!)
  setTimeout(() => {
    currentStage.value = 'invite'
  }, 10000)

  // Intersection Observers for Scroll Entrances
  const page2Element = document.getElementById('page-2')
  if (page2Element) {
    const obs2 = new IntersectionObserver(
      (entries) => {
        entries.forEach((e) => {
          if (e.isIntersecting) showPage2Events.value = true
        })
      },
      { threshold: 0.35 }
    )
    obs2.observe(page2Element)
  }

  const page3Element = document.getElementById('page-3')
  if (page3Element) {
    const obs3 = new IntersectionObserver(
      (entries) => {
        entries.forEach((e) => {
          if (e.isIntersecting) showPage3Events.value = true
        })
      },
      { threshold: 0.35 }
    )
    obs3.observe(page3Element)
  }
})

onUnmounted(() => {
  if (timerInterval) clearInterval(timerInterval)
})

function scrollToFirstPage() {
  document.getElementById('page-1')?.scrollIntoView({ behavior: 'smooth' })
}

function scrollToSecondPage() {
  document.getElementById('page-2')?.scrollIntoView({ behavior: 'smooth' })
}

function scrollToThirdPage() {
  document.getElementById('page-3')?.scrollIntoView({ behavior: 'smooth' })
}
</script>

<style scoped>
.app-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100vw;
  height: 100dvh;
  margin: 0;
  padding: 0;
  background: radial-gradient(circle, #fcfbf9 0%, #e7decb 100%);
  overflow-y: auto;
  scroll-snap-type: y mandatory;
  scroll-behavior: smooth;
}

.invite-card-wrapper {
  min-height: 100dvh;
  width: 100vw;
  display: flex;
  justify-content: center;
  align-items: center;
  scroll-snap-align: start;
  scroll-snap-stop: always;
  box-sizing: border-box;
}

.invite-card {
  position: relative;
  container-type: inline-size;
  aspect-ratio: 9 / 16;
  max-height: 98dvh;
  max-width: 100vw;
  height: 98dvh;
  width: calc(98dvh * 9 / 16);
  background-repeat: no-repeat;
  background-position: center center;
  background-size: cover;
  box-shadow: 0 10px 30px rgba(119, 107, 85, 0.15);
  transition: all 0.3s ease;
}

.page-1-bg {
  background-image: url('./assets/first_page.png');
}

.page-2-bg {
  background-image: url('./assets/second_page.png');
}

.page-3-bg {
  background-image: url('./assets/third_page.png');
}

/* PAGE 1: Inner Canvas Zone */
.kural-container {
  position: absolute;
  top: 33%;
  bottom: 40%;
  left: 24%;
  right: 28%;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  pointer-events: none;
}

.verse-wrapper {
  width: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

/* Standardized Verse Typography (larger page 1 sizes) */
.kural-tamil {
  font-family: 'Noto Serif Tamil', 'Tiro Tamil', serif;
  font-style: italic;
  font-weight: 600;
  color: #382928;
  font-size: calc(3.8cqw * var(--font-scale));
  line-height: 1.45;
  text-align: center;
  margin: 0;
  padding: 0;
  word-break: keep-all;
}

.kural-english {
  font-family: 'Cormorant Garamond', serif;
  font-style: italic;
  font-weight: 600;
  color: #382928;
  font-size: calc(3.8cqw * var(--font-scale));
  line-height: 1.4;
  text-align: center;
  margin: 0;
  padding: 0;
}

.invite-wrapper {
  gap: 0.9cqw;
}

.invite-sub {
  font-family: 'Cormorant Garamond', serif;
  font-style: italic;
  font-weight: 600;
  color: #63524b;
  font-size: calc(3.2cqw * var(--font-scale));
  letter-spacing: 0.03em;
  margin: 0;
  text-align: center;
}

.invite-names {
  font-family: 'Cinzel', serif;
  font-weight: 700;
  color: #2b1f1e;
  font-size: calc(4.0cqw * var(--font-scale));
  line-height: 1.35;
  margin: 0.5cqw 0;
  text-align: center;
  letter-spacing: 0.02em;
}

.invite-names .ampersand {
  font-family: 'Cormorant Garamond', serif;
  font-style: italic;
  font-weight: 500;
  color: #ba8d43;
  font-size: calc(4.4cqw * var(--font-scale));
  margin: 0 0.2cqw;
}

.invite-text {
  font-family: 'Cormorant Garamond', serif;
  font-style: italic;
  font-weight: 600;
  color: #483837;
  font-size: calc(3.6cqw * var(--font-scale));
  line-height: 1.45;
  margin: 0;
  text-align: center;
}

/* PAGE 2: Events Container */
.events-container {
  position: absolute;
  top: 26%;
  bottom: 26%;
  left: 18%;
  right: 18%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
  gap: 1.4cqw;
}

.events-heading {
  font-family: 'Cinzel', serif;
  font-weight: 700;
  color: #ba8d43;
  font-size: 3.4cqw;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  margin: 0 0 0.4cqw 0;
  opacity: 0;
}

.event-block {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.4cqw;
  opacity: 0;
}

.event-title {
  font-family: 'Cinzel', serif;
  font-weight: 700;
  color: #2b1f1e;
  font-size: 3.8cqw;
  letter-spacing: 0.06em;
  margin: 0;
}

.event-date {
  font-family: 'Cormorant Garamond', serif;
  font-style: italic;
  font-weight: 600;
  color: #483837;
  font-size: 3.6cqw;
  margin: 0;
}

.event-time {
  font-family: 'Cormorant Garamond', serif;
  font-weight: 600;
  color: #63524b;
  font-size: 3.4cqw;
  margin: 0;
}

.event-divider {
  margin: 0.4cqw 0;
  opacity: 0;
}


/* PAGE 3: Venue Details Container */
.venue-container {
  position: absolute;
  top: 42%;
  left: 20%;
  right: 20%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
  gap: 1.0cqw;
  opacity: 0;
}

.venue-heading {
  font-family: 'Cinzel', serif;
  font-weight: 700;
  color: #ba8d43;
  font-size: 3.2cqw;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  margin: 0;
}

.venue-title {
  font-family: 'Cinzel', serif;
  font-weight: 700;
  color: #2b1f1e;
  font-size: 3.8cqw;
  line-height: 1.35;
  letter-spacing: 0.03em;
  margin: 0;
}

.map-btn {
  display: inline-flex;
  align-items: center;
  gap: 0.5em;
  background: rgba(255, 253, 248, 0.95);
  border: 1px solid rgba(186, 141, 67, 0.5);
  color: #382928;
  font-family: 'Cormorant Garamond', serif;
  font-weight: 700;
  font-style: italic;
  font-size: 3.0cqw;
  padding: 0.45em 1.1em;
  border-radius: 20px;
  text-decoration: none;
  box-shadow: 0 4px 15px rgba(119, 107, 85, 0.15);
  transition: all 0.2s ease;
  margin-top: 0.4cqw;
}

.map-btn:hover {
  background: #ffffff;
  border-color: #ba8d43;
  color: #ba8d43;
  box-shadow: 0 6px 20px rgba(186, 141, 67, 0.3);
  transform: translateY(-2px);
}

/* PAGE 3: 3 Interlocked Gold Circles - Absolute Percentage Positioning */
.timer-circle {
  position: absolute;
  top: 63%;
  height: 14%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
  pointer-events: none;
  opacity: 0;
}

.timer-circle-days {
  left: 19.5%;
  width: 19.5%;
}

.timer-circle-hours {
  left: 40.25%;
  width: 19.5%;
}

.timer-circle-mins {
  left: 61.0%;
  width: 19.5%;
}

.timer-val {
  font-family: 'Cinzel', serif;
  font-weight: 700;
  color: #2b1f1e;
  font-size: 4.8cqw;
  line-height: 1;
}

.timer-label {
  font-family: 'Cinzel', serif;
  font-weight: 700;
  color: #ba8d43;
  font-size: 1.8cqw;
  letter-spacing: 0.08em;
  margin-top: 0.2cqw;
}

/* Navigation Buttons */
.next-page-btn {
  position: absolute;
  bottom: 4.5%;
  left: 50%;
  transform: translateX(-50%);
  background: rgba(255, 253, 248, 0.88);
  backdrop-filter: blur(8px);
  border: 1px solid rgba(186, 141, 67, 0.45);
  color: #382928;
  font-family: 'Cinzel', serif;
  font-size: 2.4cqw;
  font-weight: 700;
  letter-spacing: 0.04em;
  padding: 0.5em 1.2em;
  border-radius: 20px;
  cursor: pointer;
  display: flex;
  align-items: center;
  gap: 0.4em;
  box-shadow: 0 4px 15px rgba(119, 107, 85, 0.18);
  animation: bounce 2s infinite;
  pointer-events: auto;
  transition: all 0.2s ease;
}

.next-page-btn:hover {
  background: #ffffff;
  border-color: #ba8d43;
  box-shadow: 0 6px 20px rgba(186, 141, 67, 0.3);
}

.prev-page-btn {
  position: absolute;
  top: 3.5%;
  left: 50%;
  transform: translateX(-50%);
  background: rgba(255, 253, 248, 0.88);
  backdrop-filter: blur(8px);
  border: 1px solid rgba(186, 141, 67, 0.45);
  color: #382928;
  font-family: 'Cinzel', serif;
  font-size: 2.2cqw;
  font-weight: 700;
  letter-spacing: 0.04em;
  padding: 0.4em 1em;
  border-radius: 20px;
  cursor: pointer;
  display: flex;
  align-items: center;
  gap: 0.4em;
  box-shadow: 0 4px 15px rgba(119, 107, 85, 0.18);
  pointer-events: auto;
  transition: all 0.2s ease;
}

.prev-page-btn:hover {
  background: #ffffff;
  border-color: #ba8d43;
}

@keyframes bounce {
  0%, 20%, 50%, 80%, 100% { transform: translate(-50%, 0); }
  40% { transform: translate(-50%, -6px); }
  60% { transform: translate(-50%, -3px); }
}

/* Animations */
.event-header-anim, .page3-venue-anim {
  animation: fadeInDown 1.1s cubic-bezier(0.25, 0.46, 0.45, 0.94) forwards;
  animation-delay: 0.2s;
}

.event-block-1-anim {
  animation: fadeInUp 1.2s cubic-bezier(0.25, 0.46, 0.45, 0.94) forwards;
  animation-delay: 0.5s;
}

.event-divider-anim {
  animation: fadeIn 1.0s ease forwards;
  animation-delay: 0.9s;
}

.event-block-2-anim {
  animation: fadeInUp 1.2s cubic-bezier(0.25, 0.46, 0.45, 0.94) forwards;
  animation-delay: 1.2s;
}

.page3-timer-anim {
  animation: scaleIn 1.2s cubic-bezier(0.25, 0.46, 0.45, 0.94) forwards;
  animation-delay: 0.7s;
}

@keyframes fadeInDown {
  from {
    opacity: 0;
    transform: translateY(-16px);
    filter: blur(3px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
    filter: blur(0);
  }
}

@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(16px);
    filter: blur(3px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
    filter: blur(0);
  }
}

@keyframes scaleIn {
  from {
    opacity: 0;
    transform: scale(0.9);
    filter: blur(3px);
  }
  to {
    opacity: 1;
    transform: scale(1);
    filter: blur(0);
  }
}

/* Vue Transition */
.kural-fade-enter-active,
.kural-fade-leave-active {
  transition: all 1.2s cubic-bezier(0.25, 0.46, 0.45, 0.94);
}

.kural-fade-enter-from {
  opacity: 0;
  transform: translateY(14px);
  filter: blur(3px);
}

.kural-fade-enter-to {
  opacity: 1;
  transform: translateY(0);
  filter: blur(0);
}

.kural-fade-leave-from {
  opacity: 1;
  transform: translateY(0);
  filter: blur(0);
}

.kural-fade-leave-to {
  opacity: 0;
  transform: translateY(-14px);
  filter: blur(3px);
}

/* Laptop and Desktop Screens (Landscape) */
@media (min-width: 601px) and (min-aspect-ratio: 9/16) {
  .invite-card {
    height: 96dvh;
    width: calc(96dvh * 9 / 16);
    border-radius: 12px;
    box-shadow: 0 20px 50px rgba(119, 107, 85, 0.25);
    border: 1px solid rgba(255, 255, 255, 0.4);
  }
}

@media (min-width: 601px) and (max-aspect-ratio: 9/16) {
  .invite-card {
    width: 90vw;
    height: calc(90vw * 16 / 9);
    border-radius: 12px;
    box-shadow: 0 20px 50px rgba(119, 107, 85, 0.25);
    border: 1px solid rgba(255, 255, 255, 0.4);
  }
}
</style>
