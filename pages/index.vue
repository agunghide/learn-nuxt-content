<template>
  <main class="bg-gray-800 p-10 min-h-[100vh]">
    <h1 class="text-4xl font-bold mb-5 text-white">
      Blog Posts
    </h1>
    <SearchInput class="mb-3" />
    <ul class="flex flex-col">
      <li
        v-for="article of articles"
        :key="article.slug"
        class="w-full mb-6 rounded-lg"
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
    <div>
      <div class="inline-grid gap-3 grid-flow-col">
        <div
          v-for="page in pagination.totalPages"
          :key="`page-${page}`"
          class="py-3 px-4 rounded-md cursor-pointer"
          :class="{
            'bg-gray-400 pointer-events-none' : pagination.page === page - 1,
            'bg-white cursor-pointer' : pagination.page !== page - 1
          }"
          @click="changePage(page)"
        >
          {{ page }}
        </div>
      </div>
    </div>
  </main>
</template>

<script>
export default {
  name: 'IndexPage',
  async asyncData ({ $content }) {
    const pagination = {
      page: 1,
      perPage: 1,
      totalPages: 0
    }

    const articles = await $content('articles')
      .sortBy('createdAt', 'asc')
      .skip(pagination.page - 1)
      .limit(pagination.perPage)
      .fetch()

    const articlesLength = await $content('articles')
      .fetch()

    pagination.totalPages = articlesLength.length / pagination.perPage

    return {
      pagination,
      articles
    }
  },
  methods: {
    async changePage (page) {
      this.pagination.page = page - 1

      this.articles = await this.$content('articles')
        .sortBy('createdAt', 'asc')
        .skip(this.pagination.page)
        .limit(this.pagination.perPage)
        .fetch()
    }
  }
}
</script>
