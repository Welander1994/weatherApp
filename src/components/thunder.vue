<script setup>
</script>

<template>
    <div class="thunder">
        <div class="flash"></div>


        <img src="../assets/lightning.svg" alt="ligthning">

    </div>
    <div class="test">
        <div class="cloud"></div>
        <div class="clouds2"></div>
    </div>
</template>

<style lang="scss" scoped>
* {
    position: fixed;
    top: -5%;
    left: -10%;
    width: 120%;
    height: 105vh;
    z-index: -99;

}

.test {
    filter: blur(30px);

}

.thunder {
    img {

        transform: translateX(-18vw);
        rotate: 45deg;
        z-index: -45;
        animation: thunder 4s linear infinite;
    }

    .flash {
        background: linear-gradient(to top, rgba(255, 255, 255, 0), rgba(255, 255, 255, 0.5));
        animation: flash 4s linear infinite;
    }

}



.cloud {
    background: linear-gradient(to top, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0.5));
    opacity: 80%;
    animation: cloud 8s ease-in-out infinite;
    z-index: -50;
    height: 80vh;

}

.cloud2 {
    background: linear-gradient(to top, rgba(255, 255, 255, 0), rgba(255, 255, 255, 0.9));
    opacity: 90%;
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


@keyframes thunder {
    0% {
        opacity: 0%;
    }

    90% {
        opacity: 0%;

    }

    91% {
        opacity: 100%;

    }

    92% {
        opacity: 10%;

    }

    96% {
        opacity: 100%;

    }

    100% {
        opacity: 100%;

    }
}


@keyframes flash {
    0% {
        opacity: 0%;
    }

    88% {
        opacity: 0%;

    }

    89% {
        opacity: 100%;

    }

    91% {
        opacity: 10%;

    }

    92% {
        opacity: 0%;

    }

    100% {
        opacity: 0%;

    }
}
</style>