<template>
    <div class="p-4">
        <h1 class="text-2xl font-bold">Корзина</h1>
        <div v-if="store.cart.length === 0" class="text-gray-600">Ваша корзина пуста.</div>
        <div v-else>
            <div v-for="item in store.cart" :key="item.id" class="border-b border-gray-200 py-2">
                <div class="flex items-center justify-between">
                    <div>
                        <h2 class="text-gray-300">{{ item.name }}</h2>
                        <p class="text-gray-600">Цена: {{ item.price }} руб.</p>
                    </div>
                    <div class="flex items-center">
                        <button @click="decrementQuantity(item)"
                            class="bg-red-500 text-white px-3 py-1 rounded mr-2 ml-2">-</button>
                        <input v-model="item.quantity" type="number" min="1"
                            class="w-16 text-center border border-gray-300 px-2 py-1"
                            @change="updateQuantity(item, item.quantity)" />
                        <button @click="incrementQuantity(item)"
                            class="bg-green-500 text-white px-3 py-1 rounded ml-2">+</button>
                        <button @click="removeFromCart(item)"
                            class="bg-red-500 text-white px-3 py-1 rounded ml-4">Удалить</button>
                    </div>
                </div>
            </div>
            <p class="text-gray-300 mt-4 font-bold">Всего: {{ store.cartTotal }} рублей</p>
        </div>
        <router-link to="/" class="text-blue-500 hover:underline mt-2 block">Вернуться в Католог</router-link>
    </div>
</template>

<script setup>
import { useStore } from '../stores/shop';

const store = useStore();

const removeFromCart = (product) => {
    store.removeFromCart(product);
};

const updateQuantity = (product, quantity) => {
    if (quantity < 1) {
        product.quantity = 1;
    }
    store.updateQuantity(product, product.quantity);
};

const incrementQuantity = (product) => {
    product.quantity++;
    store.updateQuantity(product, product.quantity);
};

const decrementQuantity = (product) => {
    if (product.quantity > 1) {
        product.quantity--;
        store.updateQuantity(product, product.quantity);
    }
};
</script>