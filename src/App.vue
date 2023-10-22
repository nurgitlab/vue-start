<template>
  <div class="app">
    <h1>Страница с постами</h1>

    <middle-button @click="showDialog">
      Создать пост
    </middle-button>

    <middle-button @click="fetchUsers" v-model="isLoading">
      Получить данные!
    </middle-button>
    <MyDialog v-model:show="dialogVisible">
      <post-form
          @create="createPost"
      />
    </MyDialog>
    <h1 v-if="posts.length === 0 && isLoading === false" style="color: red">
      Постов нет!
    </h1>
    <h2 v-if="isLoading">
      Идёт загрузка!
    </h2>
    <div v-else>
      <post-list
          :posts="posts"
          @deletePost="removePost"
      />
    </div>
  </div>
</template>

<script>
import PostList from "@/components/PostList";
import PostForm from "@/components/PostForm"
import MyDialog from "@/components/UI/MyDialog";
import MiddleButton from "@/components/UI/MiddleButton";
import axios from "axios";

export default {
  components: {
    MiddleButton,
    PostForm, PostList, MyDialog,
  },
  data() {
    return {
      posts: [],
      dialogVisible: false,
      isLoading: false,
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
        const response = await axios.get(
            'https://jsonplaceholder.typicode.com/posts?_limit=5'
        )
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
</style>