<template>
  <div class="post">
    <div><strong>Название: </strong> {{title}}</div>
    <div><strong>Описание: </strong> {{text}}</div>
  </div>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      required: true,
    },
    text: {
      type: String,
      required: true,
    },
  }
}
</script>

<style scoped>
  .post {
    background: azure;
    border: 1px seagreen solid;
    padding: 15px;
  }
</style>