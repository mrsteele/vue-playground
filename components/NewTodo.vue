<template>
  <form v-on:submit="add">
    <input v-model="newTodo" placeholder="type something and press 'enter'" />
  </form>
</template>

<style scoped>
  input {
    width: 100%;
    padding: 1em;
    border: none;
    margin-bottom: 0.2em;
    font-size: 1em;
    opacity: 0.5;
    transition: all 0.2s ease-out;
    outline: none;
  }

  input:focus {
    opacity: 1;
    background: #fff;
  }
</style>

<script>
export default {
  data: () => ({
    newTodo: ''
  }),
  methods: {
    add: function (e) {
      e.preventDefault()
      this.$emit('add', this.newTodo)
      this.newTodo = ''
    }
  }
}
</script>
