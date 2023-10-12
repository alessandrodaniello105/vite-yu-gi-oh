<script>
import Header from './components/Header.vue'

export default {
  name: 'App',
  components: {
    Header
  }

}
</script>

<template>
  <h1>Hello World</h1>

  <Header />
  
</template>

<style lang="scss">

@use './scss/main.scss' as *;

</style>