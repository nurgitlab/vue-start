<template>
  <div v-for="post in posts">
    <post-item :text=post.text :title=post.title />
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
  }
}
</script>

<style scoped>

</style>