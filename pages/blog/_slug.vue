<template>
  <div class="bg-gray-800 p-10 min-h-[100vh] min-w-full">
    <nuxt-content
      class="prose prose-invert prose-hr:my-3 prose-headings:mb-3"
      :document="content"
    />
  </div>
</template>

<script>
export default {
  async asyncData ({ $content, params }) {
    const content = await $content('articles', params.slug || 'not-found').fetch()

    return { content }
  },
  head () {
    return {
      title: this.content.title || 'Learn Nuxt Content'
    }
  }
}
</script>
