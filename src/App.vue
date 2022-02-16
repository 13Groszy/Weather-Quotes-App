<template>
  <h1>Simple Weather App</h1>
  <div class="horizontal__wrapper">
    <Watch @click="changeBg()" />
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
    changeBg(){
      let bg = document.querySelector('.img');
      setInterval(function(){
        if (bg.classList.contains("one")) {
          bg.classList.add('two');
          bg.classList.remove('one');
        }else if (bg.classList.contains("two")) {
          bg.classList.add('three');
          bg.classList.remove('two');
          }
          else if (bg.classList.contains("three")) {
          bg.classList.add('four');
          bg.classList.remove('three');
          }
          else if (bg.classList.contains("four")) {
          bg.classList.add('five');
          bg.classList.remove('four');
          }
        else{
          bg.classList.add('one');
          bg.classList.remove('five');
        }
      },10000)
    }
  },
  mounted(){
    this.changeBg();
  }
}
</script>

<style lang="scss">
$mediaMinWidth: 320px;
$mediaMidWidth: 800px;
*{
  margin:0;
  padding:0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin: auto;
  padding-top:5vh;
    .horizontal__wrapper{
      display: flex;
      justify-content: center;
      gap:10vw;
    }
  h1{
    margin-bottom: 5vh;
  }
}
.img{
  position: absolute;
  width:100%;
  height: 100vh;
  z-index:-2;
  opacity:0.6;
  transition: linear 1s;
}
.one{
  background:url('./assets/img_mobile/1.jpg')center no-repeat;
  background-size: cover;
}
.two{
  background:url('./assets/img_mobile/2.jpg')center no-repeat;
  background-size: cover;
}
.three{
  background:url('./assets/img_mobile/3.jpg')center no-repeat;
  background-size: cover;
}
.four{
  background:url('./assets/img_mobile/4.jpg')center no-repeat;
  background-size: cover;
}
.five{
  background:url('./assets/img_mobile/5.jpg')center no-repeat;
  background-size: cover;
}
</style>
