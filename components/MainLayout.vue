<template>
  <main>
    <slot></slot>
  </main>
</template>

<style>
  main {
    color: #222;
    background-color: #efefef;
    font-family: Helvetica, Arial, "sans-serif";
    padding: 1.5em;
    max-width: 600px;
    margin: 20px auto;
    box-shadow: 0 0 20px 10px rgba(0, 0, 0, 0.2);
  }

  * { box-sizing: border-box; }
</style>
