<template>
  <nuxt-content
    class="prose prose-sm sm:prose lg:prose-lg xl:prose-2xl"
    :document="content"
  />
</template>

<script>
export default {
  name: 'IndexPage',
  async asyncData ({ $content, params }) {
    const content = await $content(params.slug || 'index').fetch()

    return { content }
  }
}
</script>
