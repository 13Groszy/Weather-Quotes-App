<template>
  <div>
    <Watch />
    <City :passed-city='this.cityName' />
  </div>
  <Weather @pass-city-name="passCityName" />
  <Quotes />
</template>

<script>
import Weather from './components/Weather.vue'
import Watch from './components/Watch.vue'
import Quotes from './components/Quotes.vue'
import City from './components/City.vue'

export default {
  name: 'App',
  data() {
    return {
    cityName: '',
    }
  },
  props:{
    passedCity: String
  },
  components: {
    Weather,
    Watch,
    Quotes,
    City,
  },
  methods: {
    passCityName(id){
      this.cityName = id
    }
  }
}
</script>

<style lang="scss" scope>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
