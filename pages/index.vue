<template>
  <div>
    <NavigationBar />
    <div
      class="bg-zinc-900 text-white flex flex-col items-center overflow-hidden min-h-screen position-relative"
    >
      <HomePage />
      <BreakBrick v-if="isLargeScreen" />
    </div>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  data() {
    return {
      isLargeScreen: true,
    }
  },
  mounted() {
    this.checkScreenSize()
    window.addEventListener('resize', this.checkScreenSize)
  },
  beforeDestroy() {
    window.removeEventListener('resize', this.checkScreenSize)
  },
  methods: {
    checkScreenSize() {
      this.isLargeScreen = window.innerWidth >= 768 // Adjust the breakpoint as needed
    },
  },
}
</script>

<style>
html,
body {
  background-color: #161e2e;
  margin: 0;
  padding: 0;
  height: 100%;
}
</style>
