<template>
  <div
    class="item"
    v-on:click="$emit('toggle')"
    v-bind:class="{
      completed: todo.complete,
      hidden: todo.hidden
    }"
  >
    <input type="checkbox" class="checkbox" v-model="todo.complete" /> {{ todo.text }}
    <button class="delete" type="button" v-on:click="$emit('delete')">
      &times;
    </button>
  </div>
</template>

<style scoped>
  .item {
    user-select: none;
    padding: 1em;
    background: #fff;
    margin-bottom: 0.2em;
    cursor: pointer;
    position: relative;
  }

  .item.hidden { display: none; }

  .item:hover {
    color: #999;
  }

  .checkbox {
    pointer-events: none;
  }

  .delete {
    background: none;
    border: none;
    cursor: pointer;
    font-size: 2em;
    position: absolute;
    right: 0;
    top: 50%;
    transform: translateY(-50%);
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
