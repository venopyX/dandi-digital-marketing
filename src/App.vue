<script setup>
import Home from './views/Home.vue'
import NavBar from './components/NavBar.vue'
</script>

<template>
  <div class="min-h-screen flex flex-col">
    <div class="h-0" />
    <NavBar />
    <div class="flex-1 pt-20">
      <Home />
    </div>
  </div>
</template>

<style scoped>
</style>
