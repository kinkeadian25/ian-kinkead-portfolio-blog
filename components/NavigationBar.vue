<template>
  <nav class="bg-zinc-950 text-white w-full sticky top-0 z-10">
    <div class="container mx-auto flex items-center justify-between px-4 py-4">
      <div>
        <nuxt-link to="/" class="text-2xl font-bold">Ian Kinkead</nuxt-link>
      </div>
      <div class="flex items-center">
        <button class="md:hidden ml-4 focus:outline-none" @click="toggleMenu">
          <svg
            class="w-6 h-6 text-white"
            fill="none"
            stroke="currentColor"
            viewBox="0 0 24 24"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M4 6h16M4 12h16M4 18h16"
            ></path>
          </svg>
        </button>
      </div>
      <ul class="hidden md:flex md:space-x-4">
        <li>
          <router-link to="/" class="hover:text-teal-500">Home</router-link>
        </li>
        <li>
          <nuxt-link to="/blog" class="hover:text-teal-500">Blog</nuxt-link>
        </li>
      </ul>
    </div>
    <ul
      v-if="isMenuOpen"
      class="md:hidden bg-gray-900 text-white absolute top-16 right-0 w-48 py-2 px-4 space-y-2"
    >
      <li>
        <router-link to="/" class="hover:text-teal-500">Home</router-link>
      </li>
      <li>
        <nuxt-link to="/blog" class="hover:text-teal-500">Blog</nuxt-link>
      </li>
    </ul>
  </nav>
</template>

<script>
export default {
  data() {
    return {
      isMenuOpen: false,
    }
  },
  methods: {
    toggleMenu() {
      this.isMenuOpen = !this.isMenuOpen
    },
  },
}
</script>
