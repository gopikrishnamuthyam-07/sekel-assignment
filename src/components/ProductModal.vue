<template>
  <div
    v-if="isOpen"
    class="fixed inset-0 flex items-center justify-center bg-gray-800 bg-opacity-50"
  >
    <div class="bg-white p-6 rounded-lg shadow-lg md:w-1/4 flex flex-col items-center">
        
      <img
        :src="product.api_featured_image"
        :alt="product.name"
        class=""
      />
      <h2 class="text-xl font-semibold"> {{ product.name }}</h2>
      <p class="text-gray-600 mb-2">Rs: {{ product.price }}</p>
      <div class="flex-grow">
        <button
          @click="$emit('closeModal')"
          class="bg-gray-300 rounded px-4 py-2 ml-2 font-bold hover:bg-gray-400"
        >
          Close
        </button>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";

const isOpen = ref(true);

const props = defineProps(["product", "isModalOpen"]);

const addToCart = () => {
  isOpen.value = false;
};
</script>
