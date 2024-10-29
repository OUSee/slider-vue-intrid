<script setup lang="ts">
import { provide, ref } from 'vue';
import SliderNavSection from './SliderNavSection.vue';
import TopNavBar from './TopNavBar.vue';
import VideoPlayIcon from './icons/VideoPlayIcon.vue';
const curItem = ref(1);
const videoPlay = ref(false);

provide('curItem', curItem);
provide('videoPlay', videoPlay);

const touchStartX = ref(0);
const touchEndX = ref(0);


const handleTouchStart = (event: TouchEvent) => {
    touchStartX.value = event.touches[0].clientX;
};

const handleTouchMove = (event: TouchEvent) => {
    touchEndX.value = event.touches[0].clientX;
};

const handleTouchEnd = () => {
    if ((touchStartX.value - touchEndX.value) > 150) {
        if (curItem.value < 4) { curItem.value++; } else { curItem.value = 1; }
    } else if ((touchEndX.value - touchStartX.value) >
        150) {
        if (curItem.value > 1) {
            curItem.value--;
        }
        else {
            curItem.value = 4;
        }
    }
    const activeElement = document.querySelector('.active');
    activeElement?.classList.remove('active');
};

const handleVideoClick = () => {
    videoPlay.value = !videoPlay.value;
    curItem.value = 1;
}

</script>

<template>
    <div class="container">
        <TopNavBar />
        <div @touchstart="handleTouchStart" @touchmove="handleTouchMove" @touchend="handleTouchEnd"
            class="slider-wrapper">
            <div :class="`slider-wiever pos${curItem}`">
                <VideoPlayIcon @click="handleVideoClick" v-if="!videoPlay" width="50px" height="50px"
                    style="position: absolute; top: 50%; left: 45%" />
                <img v-if="!videoPlay" src="../assets/slider/img1.png" alt="" class="video-card">

                <video v-else @click="handleVideoClick" autoplay src="../assets/video/BSD.mp4" type="video/mp4"
                    class="video-card" width="482px" height="638px" />
                <img src="../assets/slider/img2.png" alt="">
                <img src="../assets/slider/img3.png" alt="">
                <img src="../assets/slider/img4.png" alt="">
            </div>
        </div>
        <SliderNavSection :curItem="curItem" :videoPlay="videoPlay" />
    </div>


</template>

<style>
.container {
    width: 482px;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 8px;
    padding-top: 20px;
    padding-bottom: 20px;
    outline: 1px solid white;
}

.slider-wrapper {
    width: 482px;
    height: 638px;
    overflow: hidden;
    margin-bottom: 24px;
}

.slider-wrapper img {
    width: 482px;
    height: 638px;
}

.slider-wiever {
    display: flex;
    flex-direction: row;
    transition: all 0.3s ease-in-out;
}

.pos1 {
    transform: translateX(0);
}

.pos2 {
    transform: translateX(-482px);
}

.pos3 {
    transform: translateX(-964px);
}

.pos4 {
    transform: translateX(-1446px);
}
</style>
