<template>
    <div>
        <div v-if="isLoading" class="flex items-center justify-center min-h-screen">
            <div aria-label="Loading..." role="status" class="flex items-center space-x-2">
                <svg class="h-20 w-20 animate-spin stroke-gray-500" viewBox="0 0 256 256">
                    <line x1="128" y1="32" x2="128" y2="64" stroke-linecap="round" stroke-linejoin="round"
                        stroke-width="24"></line>
                    <line x1="195.9" y1="60.1" x2="173.3" y2="82.7" stroke-linecap="round" stroke-linejoin="round"
                        stroke-width="24"></line>
                    <line x1="224" y1="128" x2="192" y2="128" stroke-linecap="round" stroke-linejoin="round"
                        stroke-width="24"></line>
                    <line x1="195.9" y1="195.9" x2="173.3" y2="173.3" stroke-linecap="round" stroke-linejoin="round"
                        stroke-width="24"></line>
                    <line x1="128" y1="224" x2="128" y2="192" stroke-linecap="round" stroke-linejoin="round"
                        stroke-width="24"></line>
                    <line x1="60.1" y1="195.9" x2="82.7" y2="173.3" stroke-linecap="round" stroke-linejoin="round"
                        stroke-width="24"></line>
                    <line x1="32" y1="128" x2="64" y2="128" stroke-linecap="round" stroke-linejoin="round"
                        stroke-width="24"></line>
                    <line x1="60.1" y1="60.1" x2="82.7" y2="82.7" stroke-linecap="round" stroke-linejoin="round"
                        stroke-width="24"></line>
                </svg>
                <span class="text-4xl font-medium text-gray-500">Loading...</span>
            </div>
        </div>
        <div v-else>
            <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 xl:grid-cols-5 gap-4 text-center">
                <div v-for="product in filteredProducts.slice(0, 20)" :key="product.id" class="product-card text-center shadow-lg">
                    <ProductCard :product="product" class="cursor-pointer"></ProductCard>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
import ProductCard from "./ProductCard.vue";
import axios from "axios";
// import { useToast } from 'vue-toastification';
import { onMounted, ref, computed } from "vue";

// const toast = useToast();

const isLoading = ref(true);
const productsData = ref([]);
const filteredProducts = ref([]);

const fetchData = async () => {
    await axios
        .get("https://makeup-api.herokuapp.com/api/v1/products.json")
        .then((res) => {
            if (res.data) {
                isLoading.value = false;
                productsData.value = res.data;
                filteredProducts.value = res.data.filter(
                    (item) => item.brand == "maybelline"
                );
                console.log(filteredProducts.value);
            }
        })
        .catch((err) => console.log(`Failed to fetch products: ${err}`));
};

onMounted(() => fetchData());

const slicedProducts = computed(() => filteredProducts.value.slice(0, 20));
</script>

<style scoped>
.product-card {
    border: 1px solid #ccc;
    border-radius: 8px;
    margin: 8px;
    text-align: center;
}

.product-card img {
    max-width: 100%;
    max-height: 200px;
}

.product-details {
    margin-top: 16px;
}
</style>
