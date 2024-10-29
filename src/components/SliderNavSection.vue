<script setup lang='ts'>
import { inject, Ref } from 'vue';
import ArrowIcon from './icons/ArrowIcon.vue';
const videoPlay: Ref<boolean, boolean> = inject('videoPlay')!;
const curItem: Ref<number, number> = inject('curItem')!;

const handleNextSlide = () => {
    videoPlay.value = false;
    curItem.value != 4 ? curItem.value++ : curItem.value = 1;
    const activeElement = document.querySelector('.active');
    activeElement?.classList.remove('active');
}

const handleSetSlide = (event: Event) => {
    const target = event.target as HTMLImageElement;
    const father = target.parentNode;
    const ancestor = father?.parentNode;
    if (ancestor) {
        const children = Array.from(ancestor.children)
        const index = children.indexOf(father as Element);
        (father as Element).classList.add('active');
        curItem.value = index + 1;
        videoPlay.value = false;
        children.forEach((child, i) => {
            if (i + 1 !== curItem.value) {
                (child as Element).classList.remove('active');
            }
        });
    }


}
const handlePrevSlide = () => {
    videoPlay.value = false;
    curItem.value != 1 ? curItem.value-- : curItem.value = 4;
    const activeElement = document.querySelector('.active');
    activeElement?.classList.remove('active');
}
</script>

<template>
    <div class="slider-nav-wrapper">
        <button @click="handlePrevSlide" class="slider-btn">
            <ArrowIcon direction="left" />
        </button>
        <nav class='slider-nav-images'>
            <li @click.stop="handleSetSlide" on class="nav-option">
                <img src="../assets/slider/img1.png" alt="1" style="width: 100%;">
            </li>
            <li @click="handleSetSlide" class="nav-option">
                <img src="../assets/slider/img2.png" alt="2" style="width: 100%;">
            </li>
            <li @click="handleSetSlide" class="nav-option">
                <img src="../assets/slider/img3.png" alt="3" style="width: 100%;">
            </li>
            <li @click="handleSetSlide" class="nav-option">
                <img src="../assets/slider/img4.png" alt="4" style="width: 100%;">
            </li>
        </nav>
        <button @click="handleNextSlide" class="slider-btn">
            <ArrowIcon direction="right" />
        </button>
    </div>
</template>

<style>
.slider-nav-wrapper {
    width: 100%;
    display: flex;
    justify-content: space-between;
}

.slider-nav-images {
    width: 100%;
    display: flex;
    justify-content: space-between;
}

.nav-option {
    width: 100px;
    height: 100px;
    border-radius: 8px;
    overflow: hidden;
    transition: all 0.3s ease-in-out;
}

.nav-option:hover {
    transform: scale(1.05);
}

.active {
    outline: 1px solid white;
}

.slider-btn {
    background-color: #141414;
    border-radius: 5px;
    transition: all 0.3s ease-in-out;
}

.slider-btn:hover {
    background-color: #282828;
}
</style>