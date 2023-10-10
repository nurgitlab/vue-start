<template>
  <input
      class="input"
      type="text"
      :value="value"
      @input="e => $emit('update:value', e.target.value)"
  >
</template>

<script>
export default {
  name: "CustomInput",
  props: {
    value: [String, Number]
  },
}
</script>

<style scoped>
  .input {
    width: 100%;
    border: 1px solid seagreen;
    padding: 10px 15px;
    margin-top: 15px;
  }
</style>