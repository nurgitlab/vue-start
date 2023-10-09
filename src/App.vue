<template>
  <div class="app">
    <post-form
        @create="createPost"
    />
    <post-list
        :posts="posts"
        @deletePost="removePost"
    />
  </div>
</template>

<script>
import PostList from "@/components/PostList";
import PostForm from "@/components/PostForm"
export default {
  components: {
    PostForm, PostList
  },
  data() {
    return {
      posts: [
        {id: 1, title: 'JS', text: 'описание поста'},
        {id: 2, title: 'Angular', text: 'какой то фреймворк от гугла'},
        {id: 3, title: 'React', text: 'Самый популярный фреймворк от фейсбука'},
      ],
    }
  },
  methods: {
    createPost (post) {
      this.posts.push(post)
    },
    removePost (id) {
      this.posts = this.posts.filter(post => post.id !== id)
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


</style>