<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'

defineOptions({
  name: 'WelcomeScreen',
})

const layer = ref<HTMLElement | null>(null)

const movePlane = () => {
  const scrollY = window.scrollY

  if (layer.value) {
    layer.value.style.left = `${scrollY}px`
    console.log(layer.value.style.left)
  }
}

onMounted(() => {
  window.addEventListener('scroll', movePlane)
})

onUnmounted(() => {
  window.removeEventListener('scroll', movePlane)
})
</script>

<template>
  <div class="root">
    <div ref="layer" class="layer">
      <div class="texts">
        <div class="title">
          Начните путешествие в
          <div class="content">Исландию</div>
          прямо сейчас
        </div>
      </div>
      <img src="/images/plane.png" alt="plane" class="plane" />
    </div>
    <div class="bg bg-1"></div>
    <div class="welcome-block">
      <div class="welcome-text">
        Welcome to <br />
        <span class="transparent-text">Iceland</span>
      </div>
    </div>
    <div class="bg bg-2"></div>
  </div>
</template>

<style lang="scss" scoped>
@use '@/assets/styles/variables' as v;

.root {
  font-family: 'Poppins', serif;
  color: v.$white;
  background-color: v.$backgroundColor;
}

.layer {
  position: fixed;
  left: 0;
  height: 100vh;
  width: 100%;
  background-color: v.$backgroundColor;
}

.plane {
  position: absolute;
  z-index: 2;
  left: -50vh;
  height: 100vh;
}

.texts {
  position: absolute;
  left: 50%;
  top: 50%;
  font-family: 'Roboto', sans-serif;
  text-align: center;
  font-size: 44px;
  font-weight: 700;
  letter-spacing: 0.05em;
  transform: translate(-50%, -50%);
}

.bg {
  background-size: cover;
  background-attachment: fixed;
}

.bg-1 {
  background-image: url('/images/bg1.jpg');
  height: 240vh;
}

.bg-2 {
  background-image: url('/images/bg2.jpeg');
  height: 130vh;
}

.welcome-block {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 50vh;
}

.welcome-text {
  font-size: 3em;
  letter-spacing: 0.25em;
  text-transform: uppercase;
  font-weight: 200;
  line-height: 2.5em;
  color: v.$white;
  text-align: center;
}

.transparent-text {
  font-size: 4em;
  font-weight: 900;
  letter-spacing: 0;
  background-image: url('/images/bg2.jpeg');
  background-size: cover;
  background-attachment: fixed;
  -webkit-background-clip: text;
  background-clip: text;
  color: transparent;
}
</style>
