<template>
  <main class="bg-gray-800 p-10 min-h-[100vh]">
    <h1 class="text-4xl font-bold mb-5 text-white">
      Blog Posts
    </h1>
    <ul class="flex flex-col">
      <li
        v-for="article of articles"
        :key="article.slug"
        class="w-full px-2 mb-6 rounded-lg"
      >
        <NuxtLink
          :to="{ name: 'blog-slug', params: { slug: article.slug } }"
          class="group overflow-hidden flex bg-white rounded-lg transition-shadow duration-150 ease-in-out shadow-sm hover:shadow-xxl xxlmax:flex-col w-full"
        >
          <img
            v-if="article.img"
            width="200"
            class="group-hover:scale-105 transition-transform h-48 xxlmin:w-1/2 xxlmax:w-full object-cover rounded-tl-lg rounded-bl-lg"
            :src="article.img"
          >

          <div
            class="p-6 flex flex-col justify-between xxlmin:w-1/2 xxlmax:w-full"
          >
            <h2 class="font-bold">
              {{ article.title }}
            </h2>
            <p>by {{ article.author.name }}</p>
            <p class="font-bold text-gray-600 text-sm">
              {{ article.description }}
            </p>
          </div>
        </NuxtLink>
      </li>
    </ul>
  </main>
</template>

<script>
export default {
  name: 'IndexPage',
  async asyncData ({ $content }) {
    const articles = await $content('articles')
      .sortBy('createdAt', 'asc')
      .fetch()

    return { articles }
  }
}
</script>
