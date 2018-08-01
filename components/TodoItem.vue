<template>
  <div
    class="item"
    v-bind:class="{
      completed: todo.complete,
      hidden: todo.hidden
    }"
  >
    <input type="checkbox" v-model="todo.complete" />
    <input type="text" class="text" v-model="todo.text" />
    <button class="delete" type="button" v-on:click="$emit('delete')">
      &times;
    </button>
  </div>
</template>

<style scoped>
  .item {
    user-select: none;
    padding: 1em 0.5em;
    background: #fff;
    margin-bottom: 0.2em;
    display: flex;
    align-items: center;
  }

  .item.hidden { display: none; }

  .text {
    font-size: inherit;
    border: none;
    outline: none;
    border: solid 1px transparent;
    width: 100%;
  }

  .text:hover, .text:focus {
    border-color: #ccc;
  }

  .delete {
    background: none;
    border: none;
    cursor: pointer;
    font-size: 1em;
    opacity: 0;
    transition: opacity 0.2s ease-out;
  }

  .item:hover .delete { opacity: 0.5; }
  .delete:hover { opacity: 1; }

  .completed {
    text-decoration: line-through;
    opacity: 0.5;
  }
</style>

<script>
export default {
  props: ['todo']
}
</script>
