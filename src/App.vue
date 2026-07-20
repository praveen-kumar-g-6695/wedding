<template>
  <div class="app-container">
    <div class="invite-card">
      <div class="kural-container">
        <p class="kural-tamil">
          அன்பும் அறனும் உடைத்தாயின் இல்வாழ்க்கை<br>பண்பும் பயனும் அது.
        </p>
        <div class="kural-divider">
          <svg width="60" height="10" viewBox="0 0 60 10" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M0 5H22M38 5H60M30 2C31.6569 2 33 3.34315 33 5C33 6.65685 31.6569 8 30 8C28.3431 8 27 6.65685 27 5C27 3.34315 28.3431 2 30 2Z" stroke="#cba358" stroke-width="1.2" fill="#cba358"/>
          </svg>
        </div>
        <p class="kural-english">
          "Where love and virtue guide the way,<br>marriage finds its true purpose." ✨
        </p>
      </div>
    </div>
  </div>
</template>

<script setup>
// Static layout with clean CSS animations
</script>

<style scoped>
.app-container {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100vw;
  height: 100dvh;
  margin: 0;
  padding: 0;
  background: radial-gradient(circle, #fcfbf9 0%, #e7decb 100%);
  overflow: hidden;
}

.invite-card {
  position: relative;
  container-type: inline-size;
  aspect-ratio: 9 / 16;
  max-height: 100dvh;
  max-width: 100vw;
  height: 100dvh;
  width: calc(100dvh * 9 / 16);
  background-image: url('./assets/first_page.png');
  background-repeat: no-repeat;
  background-position: center center;
  background-size: cover;
  box-shadow: 0 10px 30px rgba(119, 107, 85, 0.15);
  transition: all 0.3s ease;
}

.kural-container {
  position: absolute;
  top: 25%;
  bottom: 27%;
  left: 15%;
  right: 19%; /* extra padding on the right to offset the peacock body */
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
  pointer-events: none;
}

.kural-tamil {
  font-family: 'Pavanam', sans-serif;
  color: #3f3231;
  font-size: 5.2cqw;
  line-height: 1.6;
  margin: 0;
  padding: 0;
  opacity: 0;
  animation: fadeInUp 1.4s cubic-bezier(0.25, 0.46, 0.45, 0.94) forwards;
  animation-delay: 1s;
}

.kural-divider {
  margin: 4% 0;
  opacity: 0;
  animation: fadeIn 1.2s ease forwards;
  animation-delay: 2.2s;
  display: flex;
  justify-content: center;
  align-items: center;
}

.kural-english {
  font-family: 'Cormorant Garamond', serif;
  font-style: italic;
  font-weight: 500;
  color: #554443;
  font-size: 4.2cqw;
  line-height: 1.5;
  margin: 0;
  padding: 0;
  opacity: 0;
  animation: fadeInUp 1.4s cubic-bezier(0.25, 0.46, 0.45, 0.94) forwards;
  animation-delay: 3s;
}

@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(15px);
    filter: blur(3px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
    filter: blur(0);
  }
}

@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
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

/* If the desktop height is extremely short but wide, fit by width/height ratio */
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
