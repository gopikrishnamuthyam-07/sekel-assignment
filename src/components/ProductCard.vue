<template>
    <div class="text-center p-2 rounded-md">
        <div class="flex flex-col group" @click="openModal">
            <div class="w-full max-w-sm bg-white rounded-lg">
                <div
                    class="aspect-h-1 aspect-w-1 w-full overflow-hidden rounded-lg bg-gray-200 xl:aspect-h-8 xl:aspect-w-7 transition-transform transform hover:shadow-lg">
                    <img :src="product.api_featured_image" alt="Product" class="h-full w-full object-cover object-center" />
                </div>
                <!-- <h3 class="mt-4 text-sm text-gray-700">{{ product.name }}</h3>
                <h2 class="text-red-500 font-semibold">{{ product.category }}</h2> -->
                <div class="px-5 pb-5">
                    <a href="#">
                        <h5 class="text-xl font-bold tracking-tight text-gray-900 dark:text-white truncate">
                            {{ product.name }}
                        </h5>
                        <h2 v-if="product.category" class="text-red-500 font-semibold italic">
                            {{ product.category }}
                        </h2>
                        <h2 v-else class="text-red-500 font-semibold italic">&nbsp;</h2>
                        <span class="text-3xl font-bold text-gray-900 dark:text-white">${{ product.price }}</span>
                    </a>
                    <div class="flex items-center mt-2.5 mb-5 justify-center">
                        <div class="flex items-center space-x-1 rtl:space-x-reverse">

                            <svg v-for="n in 5" :key="n" class="w-4 h-4 text-yellow-300" aria-hidden="true"
                                xmlns="http://www.w3.org/2000/svg" fill="currentColor" viewBox="0 0 22 20">
                                <path
                                    d="M20.924 7.625a1.523 1.523 0 0 0-1.238-1.044l-5.051-.734-2.259-4.577a1.534 1.534 0 0 0-2.752 0L7.365 5.847l-5.051.734A1.535 1.535 0 0 0 1.463 9.2l3.656 3.563-.863 5.031a1.532 1.532 0 0 0 2.226 1.616L11 17.033l4.518 2.375a1.534 1.534 0 0 0 2.226-1.617l-.863-5.03L20.537 9.2a1.523 1.523 0 0 0 .387-1.575Z" />
                            </svg>

                        </div>
                        <span
                            class="bg-blue-100 text-blue-800 text-xs font-semibold px-2.5 py-0.5 rounded dark:bg-blue-200 dark:text-blue-800 ms-3">5.0</span>
                    </div>
                    <div class="flex items-center justify-center text-center">
                        <!-- <span class="text-3xl font-bold text-gray-900 dark:text-white">${{ product.price }}</span> -->
                        <a href="#"
                            class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800">
                            Add to cart
                        </a>
                    </div>
                </div>
                <!-- <p class="mt-1 text-lg font-medium text-yellow-500">
          RS: {{ product.price }}
        </p> -->
            </div>
        </div>

        <!-- <ProductModal v-if="isModalOpen" @closeModal="closeModal" :product="product" :isModalOpen="isModalOpen"
            @click="buttonClick" /> -->
    </div>
</template>

<script setup>
import { ref } from "vue";
import { defineProps, defineEmits } from "vue";

import ProductModal from "./ProductModal.vue";

const props = defineProps({
    product: {
        type: Object,
        required: true,
    },
});

const emit = defineEmits(["add"]);

function buttonClick() {
    emit("add");
}

const isModalOpen = ref(false);

const openModal = () => {
    isModalOpen.value = true;
};

const closeModal = () => {
    isModalOpen.value = false;
};
</script>

<style scoped>
.group {
    cursor: pointer;
}

.group:hover {
    transform: scale(1.05);
    transition: transform 0.3s ease-in-out;
    padding: 8px;
}

.group:hover .transition-transform {
    transform: scale(1.1);
    transition: transform 0.3s ease-in-out;
}

/* .group:focus {
  outline: none;
} */
</style>
