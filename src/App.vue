<template>
  <AccountCarousel/>
</template>

<script>
import AccountCarousel from './components/AccountCarousel.vue'

export default {
  name: 'App',
  components: {
    AccountCarousel
  }
}
</script>

<style>
body {
  margin: 0;
  padding: 0;
  background-color: #f5f5f5;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
