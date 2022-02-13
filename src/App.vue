<template>
  <div class="horizontal__wrapper">
    <Watch />
    <City :passed-city='this.locationName' />
  </div>
    <Quotes />
    <Weather @pass-city-name="passCityName" />
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
    locationName: '',
    bgclr: 'red'
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
      this.locationName = id
    },
  }
}
</script>

<style lang="scss" scope>

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  width:90vw;
  margin: auto;
    .horizontal__wrapper{
      display: flex;
      justify-content: center;
      gap:10vw;
    }
}
</style>
