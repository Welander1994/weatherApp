<script setup>
import Weather from './components/weather.vue';
import Snow from './components/snow.vue';
import Mist from './components/mist.vue';
import Rain from './components/rain.vue';
import Clouds from './components/clouds.vue';

</script>

<template>

  <header>
    <h1>Weather App</h1>
  </header>

  <main>
    <!--  <Clouds /> -->
    <!-- <Snow /> -->
    <!-- <Mist /> -->
    <!-- <Rain /> -->
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
  font-size: 3rem;
  font-weight: 700;
  text-shadow: 0 0 32px rgba(110, 106, 106, 0.1);
}
</style>
