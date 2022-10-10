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
    top: 0;
    left: 0;
    width: 100%;
    height: 110vh;
    z-index: -99;
    filter: blur(70px);
}

.mist {
    background: linear-gradient(to bottom, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0.3));
    clip-path: polygon(29% 61.3%, 71.3% 38.5%, 100% 50%, 100% 100%, 0% 100%, 0% 42.3%);
    animation: mist2 10s ease-in-out infinite;
    z-index: -50;
}

.mist2 {
    background: linear-gradient(to bottom, rgba(255, 255, 255, 0), rgba(255, 255, 255, 0.3));
    clip-path: polygon(29% 61.3%, 71.3% 38.5%, 100% 50%, 100% 100%, 0% 100%, 0% 42.3%);
    animation: mist 8s ease-in-out infinite;
    z-index: -20;
}

@keyframes mist {
    0% {
        clip-path: polygon(29% 61.3%, 71.3% 38.5%, 100% 50%, 100% 100%, 0% 100%, 0% 42.3%);
    }

    50% {
        clip-path: polygon(29.3% 73.3%, 69.5% 69.8%, 100% 62.3%, 100% 100%, 0% 100%, 0% 70.3%);
    }

    100% {
        clip-path: polygon(29% 61.3%, 71.3% 38.5%, 100% 50%, 100% 100%, 0% 100%, 0% 42.3%);
    }
}


</style>