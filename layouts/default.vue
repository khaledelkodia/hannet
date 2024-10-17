<template>
  <div class="app-container">
    <!-- <img src="~/assets/images/clock.png" class="svg-overlay" /> -->
    <div class="app-pages">
      <Header />
      <slot />
    </div>
  </div>
</template>

<!-- <style scoped>
.app-container {
  margin: 0;
  height: 100vh;
  position: relative;
}

.svg-overlay {
  position: absolute;
  bottom: 18px;
  left: 25px;
  width: 200px;
  pointer-events: none;
  opacity: 0.1;
  z-index: 1;
  rotate: 25deg;
}

.app-pages {
  position: relative; /* لجعل رأس الصفحة فوق الـ SVG */
  z-index: 2; /* تأكد من أن الرأس فوق الـ SVG */
}
</style> -->
