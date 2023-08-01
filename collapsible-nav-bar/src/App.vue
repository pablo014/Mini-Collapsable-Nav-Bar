<script setup lang="ts">
import HelloWorld from './components/HelloWorld.vue'
import NavBar from "../lib/nav-bar.vue";
</script>

<template>
  <div>
      <NavBar class="bg-blue-300" :navLinks="['test', 'test1']">
          <template #test-open>
              test
          </template>
      </NavBar>
      <RouterView></RouterView>
  </div>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
