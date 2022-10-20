<template>
  <div class="bg-gray-800 p-10 min-h-[100vh] min-w-full">
    <nuxt-content
      class="
        prose
        max-w-none
        prose-invert
        prose-hr:my-3
        prose-headings:mb-3
      "
      :document="content"
    />
    <PrevNext :prev="prev" :next="next" />
  </div>
</template>

<script>
export default {
  async asyncData ({ $content, params, redirect, error }) {
    if (!params.slug) {
      return redirect('/')
    }
    const content = await $content('articles', params.slug)
      .fetch()
      .catch(() => {
        error({ statusCode: 404, message: 'Page not found' })
      })
    const [prev, next] = await $content('articles')
      .only(['title', 'slug'])
      .sortBy('createdAt', 'desc')
      .surround(params.slug)
      .fetch()
    return {
      content,
      prev,
      next
    }
  },
  head () {
    return {
      title: this.content.title || 'Learn Nuxt Content'
    }
  }
}
</script>
