<template>
  <div>
    <transition-group name="list-complete">
      <post-item
          v-for="post in posts"
          :post="post"
          @deletePost="(el) => $emit('deletePost', el)"
          class="list-complete-item"
          v-bind:key="post.id"
      />
    </transition-group>
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
.list-complete-item {
  transition: all 1s;
  display: inline-block;
  margin-right: 10px;
}
.list-complete-enter, .list-complete-leave-to
  /* .list-complete-leave-active до версии 2.1.8 */ {
  opacity: 0;
  transform: translateY(30px);
}
.list-complete-leave-active {
  position: absolute;
}
</style>