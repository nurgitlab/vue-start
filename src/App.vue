<template>
  <div class="app">
    <h1> Страница с постами </h1>

    <div class="app__btns">
      <middle-button @click="showDialog"> Создать пост </middle-button>

      <my-select
          v-model="selectedSort"
          :options="sortOptions"
      >

      </my-select>
    </div>

    <MyDialog v-model:show="dialogVisible">
      <post-form @create="createPost"/>
    </MyDialog>

    <h1 v-if="posts.length === 0 && isLoading === false" style="color: red"> Постов нет! </h1>
    <h2 v-if="isLoading"> Идёт загрузка! </h2>

    <div v-else>
      <post-list
          :posts="posts"
          @deletePost="removePost"
      />
    </div>
  </div>
</template>

<script>
import axios from "axios";

import PostList from "@/components/PostList";
import PostForm from "@/components/PostForm"
import MyDialog from "@/components/UI/MyDialog";
import MiddleButton from "@/components/UI/MiddleButton";
import MySelect from "@/components/UI/MySelect";

export default {
  components: {
    MySelect,
    MiddleButton,
    PostForm,
    PostList,
    MyDialog,
  },
  data() {
    return {
      posts: [],
      dialogVisible: false,
      isLoading: false,
      selectedSort: '',
      sortOptions: [
        {value: 'title', name: 'По названию'},
        {value: 'body', name: 'По содержимому'},
      ]
    }
  },
  methods: {
    createPost (post) {
      this.posts.push(post)
      this.dialogVisible = false
    },
    removePost (id) {
      this.posts = this.posts.filter(post => post.id !== id)
    },
    showDialog() {
      this.dialogVisible = true
    },
    async fetchUsers () {
      this.isLoading = true
      try {
        const response = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=5')
        setTimeout(() => {
          this.posts = response.data
          console.log(response)
        }, 2000)
      } catch (e) {
        alert('Error')
      } finally {
        this.isLoading = false
      }
    }
  },
  mounted() {
    this.fetchUsers()
  },
  watch: {
    selectedSort (newValue) {
      console.log(newValue)
    },
    dialogVisible (newValue) {
      console.log(newValue)
    }
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.app {
  padding: 20px;
}

.app__btns {
  display: flex;
  justify-content: space-between;
}
</style>