<template>
  <div id="app" class="min-h-screen flex flex-col">
    <header class="bg-gray-800 text-white p-4">
      <h1 class="text-2xl">Магазин Красок</h1>
      <nav class="mt-2">
        <router-link to="/" class="text-gray-300 hover:text-white mr-4">Католог</router-link>
        <router-link to="/cart" class="text-gray-300 hover:text-white">Корзина</router-link>
      </nav>
    </header>
    <main class="flex-1 p-4">
      <router-view></router-view>
    </main>
    <footer class="bg-gray-800 text-white p-4 text-center">
      &copy; 2024 VIE Kraski Store
    </footer>
  </div>
</template>

<script setup>
import { RouterView, RouterLink } from 'vue-router';
</script>

<style scoped>

</style>