<template>
  <div v-for="post in posts">
    <post-item :post="post" @deletePost="(el) => $emit('deletePost', el)"/>
  </div>
</template>

<script>
import PostItem from "@/components/PostItem";

export default {
  props: {
    posts: {
      type: Array,
      required: true
    },
  },
  components: {
    PostItem
  },
  emits: ['deletePost']
}
</script>

<style scoped>

</style>