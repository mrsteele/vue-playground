<template>
  <form v-on:submit="add">
    <input v-model.trim="newTodo" @input="search" placeholder="search or add a new todo item..." />
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
    },
    search: function (e) {
      this.$emit('search', this.newTodo)
    }
  }
}
</script>
