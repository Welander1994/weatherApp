<script setup>
import Rain from './rain.vue';
</script>

<template>
    <div class="thunder">
        <div class="flash"></div>
        <img src="../assets/lightning.svg" alt="ligthning">
        <Rain />
    </div>
    <div class="test">
        <div class="cloud"></div>
        <div class="cloud2"></div>
    </div>

</template>

<style lang="scss" scoped>
* {
    position: fixed;
    top: -5%;
    left: -10%;
    width: 120%;
    height: 105vh;
    z-index: -9;

}

.test {
    filter: blur(50px);

}



.thunder {
    img {
        position: fixed;
        top: -140px;
        left: -100px;
        transform: rotate(45deg);
        animation: thunder 5s linear infinite;

    }

    .flash {
        background: linear-gradient(to top, rgba(255, 255, 255, 0), rgba(255, 255, 255, 0.5));
        animation: flash 5s linear infinite;
    }
}

@media screen and (min-width: 992px) {
    .thunder {
        img {
            width: 40vw;
            transform: rotate(45deg);
        }

    }
}


.cloud {
    /* background: linear-gradient(to top, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0.5)); */

    background-color: darkgray;
    opacity: 100%;
    animation: cloud 8s ease-in-out infinite;
    height: 60vh;

}

.cloud2 {
    /* background: linear-gradient(to top, rgba(255, 255, 255, .1), rgba(255, 255, 255, 0.5)); */
    background-color: rgb(43, 43, 43);
    opacity: 20%;
    animation: cloud 5s ease-in-out infinite;
    height: 80vh;

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