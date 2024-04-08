<template class="position-relative">
  <div>
    <NavigationBar class="sticky" />
    <div class="overflow-hidden bg-zinc-900 text-white min-h-screen p-10">
      <h1 class="text-2xl font-bold mb-6 text-emerald-400 text-center">
        Welcome to my Blog!
      </h1>
      <p class="text-slate-200 mb-10 text-center mx-4 md:mx-60">
        Here you will find a collection of my open source work, projects,
        learning/research, and some random fun stuff related to technology.
        Lately, I've been exploring different aspects of programming beyond just
        building full stack web and CRUD apps, but I still spend some time
        getting better at those things every day at work and home. I'm excited
        to share my research and experiences with you through this blog. I hope
        you find it informative and enjoyable!
      </p>
      <div class="container mx-auto">
        <div
          v-for="topic in topics"
          :key="topic"
          class="mb-10 p-4 m-4 bg-black border border-emerald-800 rounded-md"
        >
          <h2 class="text-2xl font-bold mb-1 mt-1 text-center">{{ topic }}</h2>
          <ul
            class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6 overflow-auto max-h-96 custom-scrollbar pr-2"
          >
            <li
              v-for="post in getPostsByTopic(topic)"
              :key="post.slug"
              class="mt-2"
            >
              <div
                class="border-2 px-6 py-2 border-emerald-600 shadow-xl rounded-lg bg-zinc-900"
              >
                <router-link :to="`/blog/${post.slug}`">
                  <h3
                    class="text-xl text-center font-semibold mb-2 hover:text-emerald-400 hover:underline"
                  >
                    {{ post.title }}
                  </h3>
                </router-link>
                <p class="text-slate-200 mb-2 text-center">
                  {{ post.description }}
                </p>
                <p class="text-slate-200 text-sm text-center">
                  {{ post.date }}
                </p>
              </div>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $content }) {
    const posts = await $content().fetch()

    return { posts }
  },
  computed: {
    topics() {
      // Get unique topics from the posts
      const topics = [...new Set(this.posts.map((post) => post.topic))]

      return topics
    },
  },
  methods: {
    getPostsByTopic(topic) {
      // Filter posts by topic
      return this.posts.filter((post) => post.topic === topic)
    },
  },
}
</script>

<style scoped>
.custom-scrollbar::-webkit-scrollbar {
  width: 10px;
}

.custom-scrollbar::-webkit-scrollbar-track {
  background: #1a202c; /* Replace with your track color */
}

.custom-scrollbar::-webkit-scrollbar-thumb {
  background: #2d3748; /* Replace with your thumb color */
}

.custom-scrollbar::-webkit-scrollbar-thumb:hover {
  background: #4a5568; /* Replace with your hover color */
}

@media (max-width: 640px) {
  .mx-4 {
    margin-left: 1rem;
    margin-right: 1rem;
  }
}
</style>
