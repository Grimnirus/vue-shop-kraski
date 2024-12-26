<template>

    <div class="card-body mb-4 custom-shadow bg-dark text-white" style="text-align: justify">
        <img :src="product.image" :alt="product.name" class="img-thumbnail"
            style="max-width: 100%; max-height: 200px; object-fit: contain;">
        <h5 class="card-text">Цена: <strong>{{ product.price }} ₽</strong></h5>
        <h1 class="card-title">{{ product.name }}</h1>
        <p class="card-text">{{ product.description }}</p>
        <button @click="addToCart(product)"
            class="bg-blue-500 text-white px-4 py-2 rounded mt-2 hover:bg-blue-400">Добавить в
            корзину</button>
        <div>
            <div v-for="item in store.cart" :key="item.id" class="text-gray-300 py-2">
                <div v-if="item.id === product.id">в корзину добавлено: {{ item.quantity }}</div>
            </div>
        </div>
        <router-link to="/" class="text-blue-500 hover:underline mt-2 block">Обратно</router-link>
    </div>
</template>
<script setup>
import { useStore } from '../stores/shop';
import { computed } from 'vue';
import { useRoute } from 'vue-router';

const store = useStore();
const route = useRoute();
const productId = route.params.id;

const product = computed(() => {
    return store.products.find((p) => p.id == productId);
});

const addToCart = (product) => {
    store.addToCart(product);
};
</script>