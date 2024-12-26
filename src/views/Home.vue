<template>
  <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
    <div v-for="product in store.products" :key="product.id" class="bg-white rounded-lg shadow-md p-4">
      <router-link :to="{ name: 'Product', params: { id: product.id } }">
        <img :src="product.image" :alt="product.name" class="w-48 h-48 object-cover rounded-t-lg hover:bg-blue-500 ">
      </router-link>
      <h2 class="text-xl text-black font-bold">{{ product.name }}</h2>
      <p class="text-gray-600">Цена: {{ product.price }} ₽</p>
      <button @click="addToCart(product)"
        class="bg-blue-500 text-white px-4 py-2 rounded mt-2 hover:bg-blue-400">Добавить в
        корзину</button>

    </div>
  </div>
</template>

<script setup>
import { useStore } from '../stores/shop';

const store = useStore();

const addToCart = (product) => {
  store.addToCart(product);
};
</script>