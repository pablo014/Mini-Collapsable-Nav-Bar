<script setup lang="ts">
import { ref } from 'vue';

export interface NavLink {
    name: string,
    url: string,
}
export interface NavBar {
    navLinks: Array<NavLink>
    minWidth?: string | number,
    maxWidth?: string | number,
}
const props = withDefaults(defineProps<NavBar>(), {
    navLinks: () => [],
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
        class="container fixed transition-all ease-in-out duration-600 h-screen">
        <RouterLink v-for="link in navLinks" :to="link.url">
            <slots name="nav-item">
                <slot :name="`${link.name}-open`" v-if="isOpen"></slot>
                <slot :name="`${link.name}-close`" v-else></slot>
            </slots>
        </RouterLink>
</div>
</template>

<style scoped>
.container {
    z-index: 1000;
}
</style>