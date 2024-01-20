<template>
    <div class="text-center p-2">
        <div class="flex flex-col hover:cursor-pointer" @click="openModal">
            <!-- <img
        :src="product.api_featured_image"
        alt="Product"
        style="object-fit: cover; width: 250px; height: 100%"
        class="cursor-pointer"
      />
      <h2 class="text-xl font-semibold pt-2">Name: {{ product.name }}</h2>
      <p class="text-gray-600 mb-2">Rs: {{ product.price }}</p> -->

            <div class="bg-white shadow-sm">
                <div class="mx-auto max-w-2xl px-4 py-16 sm:px-6 sm:py-24 lg:max-w-7xl lg:px-8">
                    <div class="grid grid-cols-1 gap-x-6 gap-y-10 sm:grid-cols-1 lg:grid-cols-2 xl:grid-cols-1 xl:gap-x-8">
                        <a href="#" class="group">
                            <div
                                class="aspect-h-1 aspect-w-1 w-full overflow-hidden rounded-lg bg-gray-200 xl:aspect-h-8 xl:aspect-w-7">
                                <img :src="product.api_featured_image"
                                    alt="Tall slender porcelain bottle with natural clay textured body and cork stopper."
                                    class="h-full w-full object-cover object-center group-hover:opacity-75" />
                            </div>
                            <h3 class="mt-4 text-sm text-gray-700">{{ product.name }}</h3>
                            <h2 class="text-red-500 font-semibold">{{ product.category }}</h2>
                            <p class="mt-1 text-lg font-medium text-yellow-500">
                                RS: {{ product.price }}
                            </p>
                            
                        </a>
                    </div>
                </div>
            </div>
        </div>
        <ProductModal v-if="isModalOpen" @closeModal="closeModal" :product="product" :isModalOpen="isModalOpen"
            @click="buttonClick" />
    </div>
</template>

<script setup>
import { ref } from "vue";

import ProductModal from "./ProductModal.vue";

///emitting a event name called add from the child Product card component to All Products component
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
