<template>
  <form @submit.prevent>
    <CustomInput
        v-model:value="post.title"
        placeholder="Название поста"
    />
    <CustomInput
        v-model:value="post.body"
        placeholder="Описание"
    />
    <MiddleButton
        @click="createPost"
    >
      Добавить пост
    </MiddleButton>
  </form>
</template>

<script>
  export default {
    data() {
      return {
        post: {
          title: '',
          body: ''
        }
      }
    },
    methods: {
      createPost () {
        this.post.id = new Date()
        this.$emit('create', this.post)
        this.post = {
          title: '',
          body: ''
        }
      }
    },
    watch: {
      post: {
        handler(newVal) {
          console.log(newVal)
        },
        deep: true
      }
    }
  }
</script>

<style scoped>
  form {
    display: flex;
    flex-direction: column;
  }
</style>