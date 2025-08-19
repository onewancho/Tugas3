<template>
  <section class="min-h-screen bg-white text-gray-800 px-4 py-12">
    <div class="max-w-2xl mx-auto">
      <router-link to="/product" class="text-pink-400 hover:underline mb-6 inline-block">&larr; Kembali ke Produk</router-link>
      <div v-if="product">
        <img :src="product.image" :alt="product.title" class="w-full h-64 object-contain rounded-xl mb-4 bg-gray-50" />
        <h2 class="text-2xl font-bold text-pink-400 mb-2">{{ product.title }}</h2>
        <p class="text-gray-500 mb-4">{{ product.description }}</p>
        <span class="text-pink-500 font-bold text-lg">${{ product.price }}</span>
      </div>
      <div v-else class="text-center text-gray-400">Memuat detail produk...</div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'ProductDetail',
  data() {
    return {
      product: null,
    };
  },
  async created() {
    const id = this.$route.params.id;
    try {
      const res = await fetch(`https://fakestoreapi.com/products/${id}`);
      this.product = await res.json();
    } catch (e) {
      this.product = null;
    }
  },
};
</script>
