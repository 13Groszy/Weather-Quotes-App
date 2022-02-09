<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <Watch />
  <Weather />
  <Quotes />
</template>

<script>
import Weather from './components/Weather.vue'
import Watch from './components/Watch.vue'
import Quotes from './components/Quotes.vue'

export default {
  name: 'App',
  components: {
    Weather,
    Watch,
    Quotes,
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
