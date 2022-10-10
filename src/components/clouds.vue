<script setup>

</script>

<template>
    <div>
        <div class="mist"></div>
        <div class="mist2"></div>
    </div>
</template>

<style lang="scss" scoped>
* {
    position: fixed;
    top: -5%;
    left: -10%;
    width: 120%;
    height: 100vh;
    z-index: -99;
    filter: blur(30px);
}

.mist {
    background: linear-gradient(to top, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0.5));
    opacity: 60%;
    animation: cloud 8s ease-in-out infinite;
    z-index: -50;
    height: 80vh;
}

.mist2 {
    background: linear-gradient(to top, rgba(255, 255, 255, 0), rgba(255, 255, 255, 0.3));
    opacity: 80%;
    animation: cloud 5s ease-in-out infinite;
    z-index: -70;

}

@keyframes cloud {
    0% {
        clip-path: polygon(50% 0%, 100% 0%, 99.7% 43%, 69.6% 43.8%, 22.3% 38.3%, 0% 47%, 0% 0%);
    }

    50% {
        clip-path: polygon(50% 0%, 100% 0%, 99.7% 53%, 69.3% 36.3%, 22.6% 50.3%, 0% 47%, 0% 0%);
    }

    100% {
        clip-path: polygon(50% 0%, 100% 0%, 99.7% 43%, 69.6% 43.8%, 22.3% 38.3%, 0% 47%, 0% 0%);
    }
}
</style>