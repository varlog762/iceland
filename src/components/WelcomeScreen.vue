<script setup lang="ts">
defineOptions({
  name: 'WelcomeScreen',
})
</script>

<template>
  <div class="root">
    <div class="layer">
      <div class="texts">
        <div class="title">
          Начните путешествие в
          <div class="content">Исландию</div>
          прямо сейчас
        </div>
      </div>
      <img src="/images/plane.png" alt="plane" class="plane" />
    </div>
  </div>
</template>

<style lang="scss" scoped>
.root {
  font-family: 'Poppins';
}
</style>
