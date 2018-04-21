<template>
  <div class="item" v-bind:class="{ completed: complete }" v-on:click="$emit('toggle')">
    <input type="checkbox" class="checkbox" v-model="complete" /> {{ text }}
  </div>
</template>

<style scoped>
  .item {
    user-select: none;
    padding: 1em;
    background: #fff;
    margin-bottom: 0.2em;
    cursor: pointer;
  }

  .item:hover {
    color: #999;
  }

  .checkbox {
    pointer-events: none;
  }

  .completed {
    text-decoration: line-through;
    opacity: 0.5;
  }
</style>

<script>
export default {
  props: ['text', 'complete']
}
</script>
