<template>
  <main-layout>
    <h1>Todo</h1>
    <p>A simple todo app I created</p>
    <new-todo v-on:add="add" v-on:search="filter"></new-todo>
    <div>
      <todo-item
        v-for="todo in todos"
        :key="todo.id"
        :todo="todo"
        v-on:toggle="toggle(todo.id)"
      ></todo-item>
    </div>
  </main-layout>
</template>

<style scoped>
  h1, p { margin-top: 0; }
</style>

<script>
import MainLayout from '../components/MainLayout.vue'
import TodoItem from '../components/TodoItem.vue'
import NewTodo from '../components/NewTodo.vue'

export default {
  data: () => ({
    todos: [{
      id: 1,
      complete: false,
      hidden: false,
      text: 'first thing'
    }, {
      id: 2,
      complete: false,
      hidden: false,
      text: 'second thing'
    }, {
      id: 3,
      complete: false,
      hidden: false,
      text: 'third'
    }]
  }),
  components: {
    MainLayout,
    NewTodo,
    TodoItem
  },
  methods: {
    toggle: function (id) {
      const todo = this.todos.find(todo => todo.id === id)
      if (todo) {
        todo.complete = !todo.complete
      }
    },
    add: function (text) {
      this.todos.unshift({
        text,
        id: Date.now(),
        complete: false,
        hidden: false
      })
      this.filter()
    },
    filter: function (search) {
      if (search) {
        this.todos.forEach(todo => {
          todo.hidden = todo.text.toLowerCase().indexOf(search.toLowerCase()) === -1
        })
      } else {
        this.todos.forEach(todo => todo.hidden = false)
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
