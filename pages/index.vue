<template>
  <main class="bg-gray-800 p-10 min-h-[100vh]">
    <h1 class="text-4xl font-bold mb-3 text-white">
      List Blog
    </h1>
    <ul>
      <li
        v-for="(article, index) in articles"
        :key="`article-${index}`"
        class="py-2 text-blue-400 hover:text-blue-600 hover:drop-shadow-md transition-all duration-200"
      >
        <nuxt-link :to="{ name: 'blog-slug', params: { slug: article.slug } }">
          {{ article.title }}
        </nuxt-link>
      </li>
    </ul>
  </main>
</template>

<script>
export default {
  name: 'IndexPage',
  async asyncData ({ $content }) {
    const articles = await $content('articles')
      .sortBy('createdBy', 'desc')
      .fetch()

    return { articles }
  }
}
</script>

<style>

</style>
