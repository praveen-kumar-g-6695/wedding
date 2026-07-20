<template>
  <div class="app-container">
    <div class="invite-card">
      <!-- The invite card holds the background image and is responsive -->
    </div>
  </div>
</template>

<script setup>
// No script needed for this basic static setup, but we keep the structure clean for future additions
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
  background: radial-gradient(circle, #fbfaf8 0%, #e5ddcf 100%);
  overflow: hidden;
}

.invite-card {
  position: relative;
  width: 100%;
  height: 100%;
  background-image: url('./assets/first_page.png');
  background-repeat: no-repeat;
  background-position: center center;
  background-size: cover;
  box-shadow: none;
  transition: all 0.3s ease;
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
