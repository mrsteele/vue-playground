<template>
  <div>
    <h1>Hello {{ name }}!</h1>
    <p>async? {{ test }}</p>
  </div>
</template>

<script>
export default {
  data: () => {
    return { name: 'world' }
  },
  asyncData: () => {
    return {
      test: 'What?!'
    }
  },
  head () {
    return {
      title: 'hello!'
    }
  }
}
</script>
