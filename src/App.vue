<script setup>
import Weather from './components/weather.vue';
</script>

<template>
  <header>
      <h1>Weather App</h1>
  </header>

  <main>
    <Weather />
  </main>
</template>

<style scoped>
  * {
    user-select: none; 
  }

  body {
    background-color: rgba(255, 255, 255, 0.15);
  }
  h1 {
    text-align: center;
    color: #fff;
    font-size: 48px;
    font-weight: 700;
    text-shadow: 0 0 32px rgba(110, 106, 106, 0.5);
  }
</style>
