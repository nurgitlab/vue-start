<template>
  <div class="app">
    <form @submit.prevent>
      <input
          v-bind:value="title"
          @input="title = $event.target.value"
          class="input"
          type="text"
          placeholder="Название поста">
      <input
          v-bind:value="text"
          @input="text = $event.target.value"
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

    <div class="post" v-for="post in posts">
      <div><strong>Название: </strong> {{post.title}}</div>
      <div><strong>Описание: </strong> {{post.text}}</div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      posts: [
        {id: 1, title: 'JS', text: 'описание поста'},
        {id: 2, title: 'Angular', text: 'какой то фреймворк от гугла'},
        {id: 3, title: 'React', text: 'Самый популярный фреймворк от фейсбука'},
      ],
      title: '',
      text: '',
    }
  },
  methods: {
    createPost () {
      const newPost = {
        id: Date.now(),
        title: this.title,
        text: this.text
      }

      this.posts.push(newPost)

      this.title = ''
      this.text = ''
    },
  },
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.post {
  background: azure;
  border: 1px seagreen solid;
  padding: 15px;
}

.app {
  padding: 20px;
}

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