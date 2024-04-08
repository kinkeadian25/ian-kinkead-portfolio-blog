<template class="position-relative">
  <div>
    <NavigationBar />
    <div class="overflow-hidden bg-zinc-900 text-white min-h-screen p-10">
      <h1 class="text-3xl font-bold mb-6 text-emerald-400 text-center">
        {{ post.title }}
      </h1>
      <nuxt-content
        :document="post"
        class="markdown text-slate-200 mb-10 mx-4 md:mx-60"
      />
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const post = await $content(params.slug).fetch()

    return { post }
  },
}
</script>

<style scoped>
::v-deep .markdown h1 {
  font-size: 2em;
  font-weight: bold;
  margin-bottom: 0.6em;
  color: #10b981;
  text-align: center;
}

::v-deep .markdown h2 {
  font-size: 1.5em;
  font-weight: bold;
  margin-top: 1em;
  color: #10b981;
}

::v-deep .markdown img {
  display: block;
  margin: 0 auto;
}

::v-deep .markdown h3 {
  font-size: 1.5em;
  font-weight: bold;
  margin-top: 1em;
  color: #10b981;
  text-align: center;
}
::v-deep .markdown h4 {
  font-size: 1em;
  font-weight: bold;
  margin-bottom: 1em;
  text-align: center;
}

::v-deep .markdown p {
  color: #d4d4d4;
  margin-bottom: 1em;
  text-align: justify;
}

::v-deep .markdown pre {
  background-color: #1f2937;
  padding: 1em;
  border-radius: 0.5em;
  overflow-x: auto;
  border: none;
  outline: none;
}

::v-deep .markdown code[class*='language-'],
::v-deep .markdown pre[class*='language-'] {
  color: #d4d4d4;
  background: #1f2937;
  text-shadow: none;
  font-family: Consolas, Monaco, 'Andale Mono', 'Ubuntu Mono', monospace;
  font-size: 1em;
  text-align: left;
  white-space: pre;
  word-spacing: normal;
}

::v-deep .markdown .token.operator {
  background: none;
}

::v-deep .markdown a {
  color: #4489e9;
  text-decoration: underline;
}

::v-deep .markdown a:hover {
  color: #7dd3fc;
}

@media (min-width: 640px) {
  ::v-deep .markdown {
    margin-left: 2rem;
    margin-right: 2rem;
  }
}

@media (min-width: 768px) {
  ::v-deep .markdown {
    margin-left: 10rem;
    margin-right: 10rem;
  }
}
</style>
