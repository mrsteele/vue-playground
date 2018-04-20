<template>
  <main>
    <h1>Todo</h1>
    <ul class="todos">
      <li v-for="todo in todos" v-bind:class="{ completed: todo.complete }" v-on:click="toggle(todo.id)">
        {{ todo.text }}
      </li>
    </ul>
  </main>
</template>

<style>
.todos li { cursor: pointer; }
.todos li:hover { color: blue; }
.completed { text-decoration: line-through; }
</style>

<script>
export default {
  data: () => ({
    todos: [{
      id: 1,
      complete: false,
      text: 'first thing'
    }, {
      id: 2,
      complete: false,
      text: 'second thing'
    }, {
      id: 3,
      complete: false,
      text: 'third'
    }]
  }),
  methods: {
    toggle: function (id) {
      const todo = this.todos.find(todo => todo.id === id)
      if (todo) {
        console.log('here', todo)
        todo.complete = !todo.complete
      }
    }
  },
  head () {
    return {
      title: 'Todo Example'
    }
  }
}
</script>
