
<script setup>
import { ref } from 'vue';
import Footer from './components/Footer.vue';
const isMobileMenuOpen = ref(false);
</script>

<template>
  <div class="bg-white min-h-screen flex flex-col font-sans">
  <header class="sticky top-0 z-50 bg-white shadow relative">
      <nav class="flex items-center justify-between px-6 py-4">
        <div class="flex items-center gap-2">
          <router-link to="/" class="flex items-center gap-2" exact-active-class="text-pink-400">
            <span class="font-logo text-xl text-pink-500 tracking-wide font-bold">Ravaya Hijab</span>
          </router-link>
        </div>
        <ul class="hidden md:flex gap-8 text-base font-semibold">
          <li><router-link to="/" class="text-gray-700 hover:text-pink-400 transition" exact-active-class="text-pink-400">Home</router-link></li>
          <li><router-link to="/product" class="text-gray-700 hover:text-pink-400 transition" active-class="text-pink-400">Product</router-link></li>
          <li><router-link to="/portofolio" class="text-gray-700 hover:text-pink-400 transition" active-class="text-pink-400">Portofolio</router-link></li>
          <li><router-link to="/about" class="text-gray-700 hover:text-pink-400 transition" active-class="text-pink-400">About</router-link></li>
          <li><router-link to="/contact" class="text-gray-700 hover:text-pink-400 transition" active-class="text-pink-400">Contact</router-link></li>
        </ul>
        <div class="hidden md:block">
          <router-link to="/login" class="px-4 py-2 rounded bg-pink-500 text-white font-semibold hover:bg-pink-300 transition">Login</router-link>
        </div>
        <!-- Mobile menu button -->
        <div class="md:hidden">
          <button type="button" aria-label="Open menu" class="p-2 rounded text-gray-700 hover:bg-gray-100" @click="isMobileMenuOpen = !isMobileMenuOpen">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" class="h-6 w-6">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
            </svg>
          </button>
        </div>
        <!-- Mobile menu -->
        <transition name="fade">
          <div v-if="isMobileMenuOpen" class="absolute left-0 top-full w-full bg-white shadow-md md:hidden z-50">
            <ul class="flex flex-col gap-4 p-6 text-base font-semibold">
              <li><router-link to="/" class="text-gray-700 hover:text-pink-400 transition block" exact-active-class="text-pink-400" @click="isMobileMenuOpen = false">Home</router-link></li>
              <li><router-link to="/product" class="text-gray-700 hover:text-pink-400 transition block" active-class="text-pink-400" @click="isMobileMenuOpen = false">Product</router-link></li>
              <li><router-link to="/portofolio" class="text-gray-700 hover:text-pink-400 transition block" active-class="text-pink-400" @click="isMobileMenuOpen = false">Portofolio</router-link></li>
              <li><router-link to="/about" class="text-gray-700 hover:text-pink-400 transition block" active-class="text-pink-400" @click="isMobileMenuOpen = false">About</router-link></li>
              <li><router-link to="/contact" class="text-gray-700 hover:text-pink-400 transition block" active-class="text-pink-400" @click="isMobileMenuOpen = false">Contact</router-link></li>
              <li><router-link to="/login" class="px-4 py-2 rounded bg-pink-500 text-white font-semibold hover:bg-pink-300 transition block text-center" @click="isMobileMenuOpen = false">Login</router-link></li>
            </ul>
          </div>
        </transition>
      </nav>
    </header>

    <main class="flex-1">
      <router-view />
    </main>
    <Footer />
  </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Borel&family=Playwrite+HU:wght@100..400&display=swap');
.font-logo {
  font-family: "Playwrite HU", cursive;
  font-optical-sizing: auto;
  font-weight: 400;
  font-style: normal;
}
body {
  background: #fff;
  color: #222;
  font-family: 'Inter', 'Segoe UI', Arial, sans-serif;
}

.text-pink-400 {
  color: #F8BBD0;
}
.bg-pink-400 {
  background-color: #F8BBD0;
}
.hover\:bg-pink-300:hover {
  background-color: #F48FB1;
}
.hover\:text-pink-400:hover {
  color: #F8BBD0;
}
/* Fade transition for mobile menu */
.fade-enter-active, .fade-leave-active {
  transition: opacity 0.3s;
}
.fade-enter-from, .fade-leave-to {
  opacity: 0;
}
.fade-enter-to, .fade-leave-from {
  opacity: 1;
}

/* Fade transition for mobile menu */
.fade-enter-active, .fade-leave-active {
  transition: opacity 0.3s;
}
.fade-enter-from, .fade-leave-to {
  opacity: 0;
}
.fade-enter-to, .fade-leave-from {
  opacity: 1;
}
</style>
