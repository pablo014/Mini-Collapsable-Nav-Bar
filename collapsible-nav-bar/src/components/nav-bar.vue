<script setup lang="ts">
import { ref } from 'vue';
export interface NavBar {
    navLinks?: Array<string>
    minWidth?: string | number,
    maxWidth?: string | number,
}
const props = withDefaults(defineProps<NavBar>(), {
    navLinks: [],
    maxWidth: '64',
    minWidth: '20'
})
const isOpen = ref(false);
const openDrawer = () => {
    isOpen.value = true;
}
const closeDrawer = () => {
    isOpen.value = false;
}
</script>

<template>
<div
        @mouseenter="openDrawer"
        @mouseleave="closeDrawer"
        :class="isOpen ? `w-${maxWidth}` : `w-${minWidth}`"
        class="transition-all ease-in-out duration-600 bg-blue-300 h-screen">

</div>
</template>

<style scoped>

</style>