<script setup lang='ts'>
defineProps<{ direction: 'left' | 'right' | 'up' | 'down' }>()
</script>

<template>
    <div :class="direction">
        <svg width="12" height="19" viewBox="0 0 12 19" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M10 17.5L2 9.5L10 1.5" stroke="white" stroke-width="2.66667" stroke-linecap="round"
                stroke-linejoin="round" />
        </svg>
    </div>
</template>

<style scoped>
div {
    width: 20px;
    height: 20px;
}

div.left {
    transform: rotate(0deg);
}

div.right {
    transform: rotate(180deg);
}

div.up {
    transform: rotate(90deg);
}

div.down {
    transform: rotate(270deg);
}
</style>