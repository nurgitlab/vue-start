<template>
  <div class="post">
    <div><strong>Название: </strong> {{post.title}}</div>
    <div><strong>Описание: </strong> {{post.text}}</div>
    <button @click="$emit('deletePost', post.id)">Удалить пост</button>
  </div>
</template>

<script>
export default {
  props: {
    post: {
      type: Object,
      required: true
    }
  },
  emits: ['deletePost'],
}
</script>

<style scoped>
  .post {
    background: azure;
    border: 1px seagreen solid;
    padding: 15px;
  }
</style>