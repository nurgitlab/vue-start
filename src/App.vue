<template>
  <div>
    <div>Кол-во лайков <strong>{{ likes }}</strong></div>
    <div>Кол-во дизлайков <strong>{{ dislikes }}</strong></div>
    <button @click="addLike">+Like</button>
    <button @click="addDislike">+Dislikes</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      likes: 0,
      dislikes: 0,
    }
  },
  methods: {
    addLike() {
      this.likes+=1
    },
    addDislike() {
      this.dislikes+=1
    }
  }
}
</script>

<style scoped>

</style>