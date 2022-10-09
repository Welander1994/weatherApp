<script setup>
(function () {

})();
</script>

<template>
    <div class="container">
        <div class="cloud">
            <div class="rain">
                <span style="--i:11"></span>
                <span style="--i:12"></span>
                <span style="--i:10"></span>
                <span style="--i:14"></span>
                <span style="--i:18"></span>
                <span style="--i:16"></span>
                <span style="--i:19"></span>
                <span style="--i:30"></span>
                <span style="--i:11"></span>
                <span style="--i:15"></span>
                <span style="--i:10"></span>
                <span style="--i:14"></span>
                <span style="--i:18"></span>
                <span style="--i:16"></span>
                <span style="--i:19"></span>
                <span style="--i:30"></span>
                <span style="--i:15"></span>
                <span style="--i:21"></span>
                <span style="--i:16"></span>
                <span style="--i:12"></span>
                <span style="--i:28"></span>
                <span style="--i:16"></span>
                <span style="--i:19"></span>
                <span style="--i:30"></span>
                <span style="--i:11"></span>
                <span style="--i:12"></span>
                <span style="--i:10"></span>

            </div>
        </div>
    </div>
</template>



<style lang="scss" scoped>
* {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100vh;
    z-index: -99;
}

.cloud {
    display: flex;
}

.rain {
    position: relative;
    display: inline-flex;
    z-index: 1;
    width: 100vw;
    display: flex;
    justify-content: space-around;
}

.rain span {
    position: relative;
    bottom: 10px;
    width: 3px;
    height: 40px;
    background: linear-gradient(to bottom, rgba(255, 255, 255, 0), rgba(255, 255, 255, 0.25));
    transform-origin: bottom;
    animation: rain 100s linear infinite;
    animation-duration: calc(15s / var(--i));
}



@keyframes rain {
    0% {
        transform: translateY(0) scale(1);
        border-radius: 50%;
    }

    90% {
        transform: translateY(85vh) scale(1);

    }

    95% {
        transform: translateY(85vh) scalex(7) scaleY(-.1);
        border-radius: 50%;
        opacity: 100%;
    }

    100% {

        transform: translateY(85vh) scalex(7) scaleY(-.2);
        border-radius: 50%;
        opacity: 0%;
    }
}
</style>