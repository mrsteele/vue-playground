<template>
  <div>
    <header>
      <span>
        Fiddle
      </span>

      <button v-on:click="run">
        Run
      </button>
    </header>
    <main>
      <aside>
        <textarea class='html' v-model='html'></textarea>
        <textarea class='css' v-model='css'></textarea>
        <textarea class='js' v-model='js'></textarea>
      </aside>
      <aside class='evaluted' v-html='evaluated'></aside>
    </main>
  </div>
</template>

<style>
  * {
    box-sizing: border-box;
  }

  html, body, div, #__nuxt, #__layout {
    padding: 0;
    margin: 0;
    height: 100%;
    font-family: Helvetica, Arial, 'sans-serif';
  }

  div {
    display: flex;
    flex-direction: column;
  }

  header {
    padding: 0.5em 1em;
    background: #6b4f2b;
    color: #efefef;
    font-size: 1.5em;
    display: flex;
  }

  header button {
    margin-left: auto;
    background: #0a0;
    border: none;
    border-radius: 3px;
    color: #efefef;
    padding: 0.25em 1em;
    font-size: 0.75em;
    cursor: pointer;
    opacity: 0.8;
    outline: none;
  }

  header button:hover {
    opacity: 1;
  }

  main {
    background: #efefef;
    display: flex;
    width: 100%;
    height: 100%;
  }

  aside {
    width: 100%;
    resize: horizontal;
    display: flex;
    flex-direction: column;
  }

  textarea {
    resize: vertical;
    overflow: auto;
    height: 34%;
    border: solid 1px #ccc;
    background: #222;
    color: #efefef;
    outline: none;
    padding: 1em;
    position: relative;
    font-size: 1em;
  }

  textarea:after {
    position: absolute;
    top: 0;
    right: 0;
    background-color: #ccc;
    padding: 0.5em;
    content: 'test';
    display: block;
  }

  .evaluted {
    padding: 1em;
    width: 100%;
    height: 100%;
    background-color: white;
  }
</style>

<script>
  const initialHTML = `<p>
    This is <strong>cool</strong>
  </p>`
  
  const run = (html, css, js) => `
  <style>
    ${css}
  </style>

  <div>${html}</div>
  `

  export default {
    data: () => ({
      html: initialHTML,
      css: '',
      js: '',
      evaluated: run(initialHTML)
    }),
    methods: {
      run () {
        this.evaluated = run(this.html, this.css, this.js)
      }
    }
  }
</script>
