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
        class="container fixed transition-all ease-in-out duration-600 bg-blue-300 h-screen">
        <RouterLink v-for="link in navLinks" :to="link">
            <slots name="nav-item">
                <slot :name="`${link}-open`" v-if="isOpen"></slot>
                <slot :name="`${link}-close`" v-else></slot>
            </slots>
        </RouterLink>
</div>
</template>

<style scoped>
.container {
    z-index: 1000;
}
</style>