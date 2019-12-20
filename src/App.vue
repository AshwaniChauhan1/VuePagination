<template>
  <div id="app">
    <pagination/>
  </div>
</template>

<script>
import pagination from '@/components/pagination.vue'

export default {
  name: 'app',
  components: {
    pagination
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
