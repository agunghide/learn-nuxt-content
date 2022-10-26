<template>
  <div>
    <img :src="author.image">
    <div>
      <h4>Author</h4>
      <p>{{ author.name }}</p>
      <p>{{ author.bio }}</p>
      {{ text }}
    </div>
  </div>
</template>
<script>
export default {
  props: {
    author: {
      type: Object,
      required: false,
      // eslint-disable-next-line vue/require-valid-default-prop
      default: () => {}
    },
    text: {
      type: String,
      default: ''
    }
  }
}
</script>
