<template>
  <section class="min-h-screen bg-white text-gray-800 px-4 py-12">
    <div class="max-w-5xl mx-auto">
      <h2 class="text-4xl font-bold text-pink-400 mb-10 text-center">Produk Ravaya Hijab</h2>
      <div class="flex flex-col md:flex-row md:items-center md:justify-between gap-4 mb-6">
        <input v-model="search" type="text" placeholder="Cari produk..." class="border rounded px-4 py-2 w-full md:w-1/3 focus:outline-none focus:ring focus:border-pink-400" />
        <div class="flex gap-2 items-center">
          <label for="perPage" class="text-gray-600">Tampil:</label>
          <select v-model="perPage" id="perPage" class="border rounded px-2 py-1 focus:outline-none focus:ring focus:border-pink-400">
            <option :value="5">5</option>
            <option :value="10">10</option>
            <option :value="20">20</option>
          </select>
          <span class="text-gray-400">item / halaman</span>
        </div>
      </div>
      <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-8">
        <template v-if="loading">
          <div v-for="n in perPage" :key="n" class="bg-white border rounded-xl shadow-lg p-6 flex flex-col items-center animate-pulse">
            <div class="w-full max-w-lg h-64 rounded-xl mb-4 bg-gray-200"></div>
            <div class="h-6 w-3/4 bg-gray-200 rounded mb-2"></div>
            <div class="h-4 w-full bg-gray-200 rounded mb-2"></div>
            <div class="h-6 w-1/4 bg-gray-200 rounded"></div>
          </div>
        </template>
        <template v-else>
          <div v-for="product in paginatedProducts" :key="product.id" class="bg-white border rounded-xl shadow-lg p-6 flex flex-col items-center">
            <img :src="product.image" :alt="product.title" class="w-full max-w-lg h-64 object-contain rounded-xl mb-4 bg-gray-50" />
            <router-link :to="`/product/${product.id}`" class="text-lg font-semibold text-pink-400 mb-2 text-center cursor-pointer hover:underline block">{{ product.title }}</router-link>
            <p class="text-gray-500 text-sm mb-2 text-center">{{ truncateDescription(product.description) }}</p>
            <span class="text-pink-500 font-bold text-lg">${{ product.price }}</span>
          </div>
        </template>
      </div>
      <div class="flex justify-center items-center gap-2 mt-8">
        <button @click="prevPage" :disabled="page === 1" class="px-3 py-1 rounded bg-pink-400 text-white font-semibold hover:bg-pink-500 transition disabled:opacity-50">Prev</button>
        <span class="text-gray-700">Halaman {{ page }} dari {{ totalPages }}</span>
        <button @click="nextPage" :disabled="page === totalPages" class="px-3 py-1 rounded bg-pink-400 text-white font-semibold hover:bg-pink-500 transition disabled:opacity-50">Next</button>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Product',
  data() {
    return {
      products: [],
      search: '',
      perPage: 5,
      page: 1,
      loading: false,
  // selectedProduct: null,
    };
  },
  computed: {
    filteredProducts() {
      if (!this.search) return this.products;
      const s = this.search.toLowerCase();
      return this.products.filter(p =>
        p.title.toLowerCase().includes(s) ||
        p.description.toLowerCase().includes(s)
      );
    },
    totalPages() {
      return Math.ceil(this.filteredProducts.length / this.perPage) || 1;
    },
    paginatedProducts() {
      const start = (this.page - 1) * this.perPage;
      return this.filteredProducts.slice(start, start + this.perPage);
    },
  },
  watch: {
    perPage() {
      this.page = 1;
    },
    search() {
      this.page = 1;
    }
  },
  methods: {
    async fetchProducts() {
      this.loading = true;
      try {
        const res = await fetch('https://fakestoreapi.com/products');
        const data = await res.json();
        this.products = data;
      } catch (e) {
        this.products = [];
      }
      this.loading = false;
    },
    nextPage() {
      if (this.page < this.totalPages) this.page++;
    },
    prevPage() {
      if (this.page > 1) this.page--;
    },
    truncateDescription(desc) {
      if (!desc) return '';
      if (desc.length <= 150) return desc;
      return desc.slice(0, 150) + '...';
    },
  },
  mounted() {
    this.fetchProducts();
  },
};
</script>
