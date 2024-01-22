<template>
  <div>
    <nav class="bg-white text-black shadow-lg">
      <div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
        <div class="flex items-center justify-between h-16">
          <div class="flex-shrink-0">
            <a href="https://sekel.tech/" target="_blank">
              <img class="h-8 w-auto" src="../assets/sekel-logo.png" alt="Sekel Logo Image" />
            </a>
          </div>
          <div class="hidden sm:flex sm:items-center sm:space-x-4">
            <a href="https://sekel.tech/data-platform" target="_blank"
              class="text-black hover:border-b-2 hover:border-black px-3 py-2 text-sm font-medium">Data Platform</a>
            <a href="https://sekel.tech/discovery-platform" target="_blank"
              class="text-black hover:border-b-2 hover:border-black px-3 py-2 text-sm font-medium">Discovery Platform</a>
            <a href="https://sekel.tech/demand-generation-platform" target="_blank"
              class="text-black hover:border-b-2 hover:border-black px-3 py-2 text-sm font-medium">Demand Generation
              Platform</a>
            <a href="https://sekel.tech/advantages-for/online-offline" target="_blank"
              class="text-black hover:border-b-2 hover:border-black px-3 py-2 text-sm font-medium">Advantages For</a>
            <a href="https://sekel.tech/company/about-us" target="_blank"
              class="text-black hover:border-b-2 hover:border-black px-3 py-2 text-sm font-medium">Company</a>
          </div>

          <div class="ml-3">
            <a href="https://app.sekel.tech/login" target="_blank"
              class="block px-4 py-2 font-semibold w-32 h-10 text-center rounded-full text-sm bg-gradient-to-r from-yellow-400 via-yellow-500 to-yellow-600 text-white"
              role="menuitem" tabindex="-1" id="user-menu-item-0">Login</a>
          </div>



          <div class="sm:hidden">
            <!-- Mobile menu button -->
            <button @click="toggleMobileMenu" type="button"
              class="inline-flex items-center justify-center p-2 text-gray-500 hover:text-black hover:bg-gray-100 focus:outline-none focus:ring focus:border-blue-300">
              <span class="sr-only">Open main menu</span>
              <svg class="h-6 w-6" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24"
                stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16m-7 6h7"></path>
              </svg>
            </button>
          </div>
        </div>
      </div>

      <!-- Mobile menu, show/hide based on menu state. -->
      <div v-show="isMobileMenuOpen" class="sm:hidden" id="mobile-menu">
        <div class="px-2 pt-2 pb-3 space-y-1">
          <a href="https://sekel.tech/" target="_blank"
            class="text-black block px-3 py-2 rounded-md text-base font-medium">Sekel tech</a>
          <a href="https://sekel.tech/data-platform" target="_blank"
            class="block px-3 py-2 rounded-md text-base font-medium">Data Platform</a>
          <a href="https://sekel.tech/discovery-platform" target="_blank"
            class="text-black block px-3 py-2 rounded-md text-base font-medium">Discovery Platform</a>
          <a href="https://sekel.tech/demand-generation-platform" target="_blank"
            class="text-black block px-3 py-2 rounded-md text-base font-medium">Demand Generation Platform
          </a>
          <a href="https://sekel.tech/advantages-for/online-offline" target="_blank"
            class="text-black block px-3 py-2 rounded-md text-base font-medium">Advantages For
          </a>
          <a href="https://sekel.tech/company/about-us" target="_blank"
            class="text-black block px-3 py-2 rounded-md text-base font-medium">Company
          </a>
        </div>
      </div>
    </nav>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const isMobileMenuOpen = ref(false);

const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value;
};
</script>
