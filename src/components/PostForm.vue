<template>
  <form @submit.prevent>
    <input
        v-model="post.title"
        class="input"
        type="text"
        placeholder="Название поста">
    <input
        v-model="post.text"
        class="input"
        type="text"
        placeholder="Описание">
    <button
        class="btn"
        @click="createPost"
    >
      Создать пост
    </button>
  </form>
</template>

<script>
  export default {
    data() {
      return {
        post: {
          title: '',
          text: ''
        }
      }
    },
    methods: {
      createPost () {
        this.post.id = new Date()
        this.$emit('create', this.post)
        this.post = {
          title: '',
          text: ''
        }
      }
    }
  }
</script>

<style scoped>
form {
  display: flex;
  flex-direction: column;
}

.btn {
  margin: 15px 0;
  align-self: flex-end;
  color: teal;
  background: none;

  padding: 10px 15px;
}

.input {
  width: 100%;
  border: 1px solid seagreen;
  padding: 10px 15px;
  margin-top: 15px;
}
</style>