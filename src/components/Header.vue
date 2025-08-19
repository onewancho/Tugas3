<template>
  <header class="bg-white text-gray-800">
    <nav class="flex justify-between items-center px-8 py-4">
      <div class="text-2xl font-bold text-pink-500">Ravaya Hijab</div>
      <ul class="flex gap-6">
  <li><router-link to="/" class="hover:text-pink-400" exact-active-class="text-pink-400">Home</router-link></li>
  <li><router-link to="/product" class="hover:text-pink-400" active-class="text-pink-400">Product</router-link></li>
  <li><router-link to="/portofolio" class="hover:text-pink-400" active-class="text-pink-400">Portofolio</router-link></li>
  <li><router-link to="/about" class="hover:text-pink-400" active-class="text-pink-400">About Us</router-link></li>
  <li><router-link to="/contact" class="hover:text-pink-400" active-class="text-pink-400">Contact Us</router-link></li>
  <li><router-link to="/login" class="hover:text-pink-400">Login</router-link></li>
      </ul>
    </nav>
  </header>
</template>

<script>
export default {
  name: 'Header',
};
</script>
