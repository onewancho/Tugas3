<template>
  <section class="min-h-screen bg-white flex flex-col items-center justify-center px-4 py-16">
    <div class="max-w-3xl w-full text-center">
      <div class="relative mx-auto mb-8 w-full max-w-2xl h-80">
        <transition name="fade" mode="out-in">
          <img
            :src="images[currentImage]"
            :key="images[currentImage]"
            alt="Ravaya Hijab"
            class="rounded-xl shadow-lg w-full h-80 object-cover object-top"
          />
        </transition>
<!-- /* Fade transition for carousel */
.fade-enter-active, .fade-leave-active {
  transition: opacity 0.7s;
}
.fade-enter-from, .fade-leave-to {
  opacity: 0;
}
.fade-enter-to, .fade-leave-from {
  opacity: 1;
} -->
        <button @click="prevImage" class="absolute left-2 top-1/2 -translate-y-1/2 bg-white bg-opacity-70 rounded-full p-2 shadow hover:bg-pink-100">
          <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" class="h-6 w-6 text-pink-400">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
          </svg>
        </button>
        <button @click="nextImage" class="absolute right-2 top-1/2 -translate-y-1/2 bg-white bg-opacity-70 rounded-full p-2 shadow hover:bg-pink-100">
          <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" class="h-6 w-6 text-pink-400">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
          </svg>
        </button>
        <div class="absolute bottom-2 left-0 right-0 flex justify-center gap-2">
          <span v-for="(img, idx) in images" :key="idx" :class="[idx === currentImage ? 'bg-pink-400' : 'bg-gray-300', 'w-3 h-3 rounded-full inline-block']"></span>
        </div>
      </div>
      <h1 class="text-5xl font-bold text-pink-400 mb-6">Selamat Datang di Ravaya Hijab</h1>
      <p class="text-lg text-gray-500 mb-8">Brand hijab modern yang mengutamakan kualitas, kenyamanan, dan gaya. Temukan koleksi terbaik kami untuk tampil cantik dan percaya diri setiap hari.</p>
      <div class="flex flex-col sm:flex-row gap-4 justify-center">
        <RouterLink to="/product" class="px-6 py-3 rounded bg-pink-400 text-white font-semibold hover:bg-pink-500 transition">Lihat Produk</RouterLink>
        <RouterLink to="/about" class="px-6 py-3 rounded border border-pink-400 text-pink-400 font-semibold hover:bg-pink-50 transition">Tentang Kami</RouterLink>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Home',
  data() {
    return {
      images: [
        'https://www.zalora.co.id/blog/wp-content/uploads/2023/09/tutorial-hijab-segi-empat.jpg',
        'https://assets.unileversolutions.com/v1/134459373.jpg',
        'https://i0.wp.com/zaloraadmin.wpcomstaging.com/wp-content/uploads/2024/01/jilbab-segi-empat-motif-branded.png?fit=1200%2C620&ssl=1',
      ],
      currentImage: 0,
      intervalId: null,
    };
  },
  mounted() {
    this.startCarousel();
  },
  beforeUnmount() {
    clearInterval(this.intervalId);
  },
  methods: {
    nextImage() {
      this.currentImage = (this.currentImage + 1) % this.images.length;
    },
    prevImage() {
      this.currentImage = (this.currentImage - 1 + this.images.length) % this.images.length;
    },
    startCarousel() {
      this.intervalId = setInterval(() => {
        this.nextImage();
      }, 3500);
    },
  },
};
</script>
