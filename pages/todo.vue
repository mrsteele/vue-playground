<template>
  <main-layout>
    <input class="title" type="text" v-model="title" />
    <new-todo v-on:add="add" v-on:search="filter"></new-todo>
    <div class="todos">
      <todo-item
        v-for="todo in todos"
        :key="todo.id"
        :todo="todo"
        v-on:delete="remove(todo.id)"
      ></todo-item>
    </div>

    <footer>Made as an experiment by <a href="https://twitter.com/matt_r_steele" target="_blank">Matthew Steele</a>.</footer>
  </main-layout>
</template>

<style scoped>
  .title {
    background: none;
    border: none;
    font-size: 2em;
    margin-bottom: 0.5em;
    outline: none;
    border: solid 1px transparent;
    width: 100%;
  }

  .title:hover { border-color: #ccc; }

  .todos { margin-bottom: 2em; }

  footer {
    text-align: center;
    font-size: 0.8em;
    color: #999;
  }

  footer a { color: inherit; }
  footer a:hover { text-decoration: none; }
</style>

<script>
import MainLayout from '../components/MainLayout.vue'
import TodoItem from '../components/TodoItem.vue'
import NewTodo from '../components/NewTodo.vue'

export default {
  data: () => ({
    title: 'Todos',
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
    add: function (text) {
      this.todos.unshift({
        text,
        id: Date.now(),
        complete: false,
        hidden: false
      })
      this.filter()
    },
    remove: function (id) {
      const i = this.todos.findIndex(todo => todo.id === id)
      this.todos.splice(i, 1)
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
