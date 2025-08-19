<template>
  <section class="min-h-screen bg-white text-gray-800 flex items-center justify-center px-4 py-12">
    <form v-if="!showRegister" class="bg-white border rounded-xl shadow-lg p-8 w-full max-w-sm mb-6">
      <h2 class="text-3xl font-bold text-pink-400 mb-6 text-center">Login</h2>
      <div class="mb-4">
        <label class="block mb-2 text-gray-700 font-semibold">Email</label>
        <input type="email" class="w-full p-2 rounded border border-pink-400 focus:outline-none focus:ring-2 focus:ring-pink-400" />
      </div>
      <div class="mb-6">
        <label class="block mb-2 text-gray-700 font-semibold">Password</label>
        <input type="password" class="w-full p-2 rounded border border-pink-400 focus:outline-none focus:ring-2 focus:ring-pink-400" />
      </div>
      <button type="submit" class="bg-pink-400 text-white px-4 py-2 rounded font-bold w-full hover:bg-pink-300 transition mb-4">Login</button>
      <div class="text-center">
        <span class="text-gray-600">Don't Have an Account?</span>
        <button @click.prevent="showRegister = true" type="button" class="text-pink-400 font-semibold hover:underline ml-2">Sign Up</button>
      </div>
    </form>
    <form v-else class="bg-white border rounded-xl shadow-lg p-8 w-full max-w-sm mb-6">
      <h2 class="text-2xl font-bold text-pink-400 mb-6 text-center">Register</h2>
      <div class="mb-4">
        <label class="block mb-2 text-gray-700 font-semibold">Email</label>
        <input type="email" class="w-full p-2 rounded border border-pink-400 focus:outline-none focus:ring-2 focus:ring-pink-400" />
      </div>
      <div class="mb-4">
        <label class="block mb-2 text-gray-700 font-semibold">Password</label>
        <input type="password" class="w-full p-2 rounded border border-pink-400 focus:outline-none focus:ring-2 focus:ring-pink-400" />
      </div>
      <div class="mb-6">
        <label class="block mb-2 text-gray-700 font-semibold">Confirm Password</label>
        <input type="password" class="w-full p-2 rounded border border-pink-400 focus:outline-none focus:ring-2 focus:ring-pink-400" />
      </div>
      <button type="submit" class="bg-pink-400 text-white px-4 py-2 rounded font-bold w-full hover:bg-pink-300 transition mb-4">Sign Up</button>
      <div class="text-center">
        <span class="text-gray-600">Do You Have account?</span>
        <button type="button" @click="showRegister = false" class="text-pink-400 font-semibold hover:underline ml-2">Login</button>
      </div>
    </form>
  </section>
</template>

<script>
export default {
  name: 'Login',
  data() {
    return {
      showRegister: false,
    };
  },
};
</script>
