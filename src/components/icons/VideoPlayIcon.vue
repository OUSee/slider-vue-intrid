<script setup lang="ts">
defineProps<{ width: string, height: string }>();

</script>

<template>
    <svg :width="width" :height='height' viewBox="0 0 44 44" fill="none" xmlns="http://www.w3.org/2000/svg">
        <circle cx="22" cy="22" r="21" stroke="white" stroke-width="2" />
        <path
            d="M31.5 19.4019C33.5 20.5566 33.5 23.4434 31.5 24.5981L19.5 31.5263C17.5 32.681 15 31.2376 15 28.9282L15 15.0718C15 12.7624 17.5 11.319 19.5 12.4737L31.5 19.4019Z"
            fill="white" />
    </svg>
</template>