./
<script setup lang='ts'>
import ContentIcon from './icons/ContentIcon.vue';
import HouseIcon from './icons/HouseIcon.vue';
import PhotoIcon from './icons/PhotoIcon.vue';
import VidICon from './icons/VidICon.vue';
</script>

<template>
    <nav class='top-nav-bar'>
        <li id="photo-option">
            <PhotoIcon op="" />
            Фото
        </li>
        <li id="video-option">
            <VidICon :op="60" />
            Видео
        </li>
        <li id="interior-option">
            <HouseIcon :op="60" />
            Интерьер
        </li>
        <li id="content-option">
            <ContentIcon :op="60" />
            Контент
        </li>
    </nav>
</template>

<style>
.top-nav-bar {
    width: 100%;
    display: flex;
    flex-direction: row;
    color: white;
    list-style: none;
    cursor: not-allowed;
}

.top-nav-bar li {
    width: 25%;
    display: flex;
    flex-direction: row;
    padding: 10px;
    font-size: 16px;
    line-height: 20px;
    gap: 8px;
    justify-content: center;
    color: #ffffff60;
    border-bottom: 2px solid #ffffff60;
}

#photo-option {
    color: #ffffff;
    border-bottom: 2px solid white;
}

#content-option {
    color: #125a49;
}
</style>