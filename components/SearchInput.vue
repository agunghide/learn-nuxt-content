<template>
  <div class="relative">
    <input
      v-model="searchQuery"
      type="search"
      autocomplete="off"
      placeholder="Search Articles"
      class="block w-full px-3 py-2 truncate leading-5 placeholder-gray-500 border border-gray-500 text-gray-700 focus:border-gray-300 rounded-md focus:outline-none focus:bg-white bg-white"
      :class="{ 'rounded-b-none' : articles.length && isFocusedSearchInput }"
      @focus="onFocusInput"
      @blur="onBlurInput"
      @keyup.up="previousListItem"
      @keyup.down="nextListItem"
      @keyup.enter="onPressEnter"
    >
    <ul
      v-if="articles.length && isFocusedSearchInput"
      class="z-10 absolute w-full flex-1 bg-white rounded-b-md border border-gray-300 overflow-hidden shadow-sm shadow-gray-700"
    >
      <li
        v-for="(article, index) of articles"
        :key="article.slug"
        :class="{ 'active' : activeList === index + 1}"
        @mouseover="activeList = index + 1"
        @mouseleave="activeList = 0"
      >
        <NuxtLink
          :to="{ name: 'blog-slug', params: { slug: article.slug } }"
          class="flex px-4 py-2 items-center leading-5 transition ease-in-out duration-150 text-gray-600 hover:text-gray-700"
        >
          {{ article.title }}
        </NuxtLink>
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  data () {
    return {
      searchQuery: '',
      articles: [],
      isFocusedSearchInput: false,
      activeList: 0 // not selected anythings
    }
  },
  watch: {
    async searchQuery (searchQuery) {
      if (!searchQuery) {
        this.articles = []
        return
      }
      this.articles = await this.$content('articles')
        .limit(6)
        .search(searchQuery)
        .fetch()
    }
  },
  methods: {
    onFocusInput () {
      this.isFocusedSearchInput = true
    },
    onBlurInput () {
      this.isFocusedSearchInput = false
      this.activeList = 0
    },
    nextListItem () {
      this.activeList = this.activeList === this.articles.length ? 1 : this.activeList + 1
    },
    previousListItem () {
      this.activeList = this.activeList === 1 ? this.articles.length : this.activeList - 1
    },
    onPressEnter () {
      if (this.activeList === 0) { return false }

      this.$router.push({ name: 'blog-slug', params: { slug: this.articles[this.activeList - 1].slug } })
    }
  }
}
</script>

<style scoped>
.active {
  @apply bg-gray-300
}
</style>
