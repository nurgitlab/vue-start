<template>
  <button
      class="btn"
  >
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: "MiddleButton"
}
</script>

<style scoped>
.btn {
  margin: 15px 0;
  align-self: flex-end;
  color: teal;
  background: none;

  padding: 10px 15px;
}
</style>