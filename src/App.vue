<template>
  <h1>Simple Weather App</h1>
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
      let bg_one = document.querySelector('.one');
      let bg_two = document.querySelector('.two');
      setInterval(function(){
        if (bg_one.classList.contains("opacity_zero")) {
          bg_one.classList.remove("opacity_zero");
          bg_two.classList.add("opacity_zero")
        }
        else{
          bg_two.classList.remove("opacity_zero");
          bg_one.classList.add("opacity_zero")
        }
      },10000)
    }
  },
  created(){
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
  width:600px;
  max-width:90%;
    .horizontal__wrapper{
      display: flex;
      justify-content: center;
      gap:10vw;
      margin-bottom: 3vh;
    }
  h1{
    margin-bottom: 5vh;
  }
}
.bg__img{
  position: absolute;
  width:100%;
  z-index:-1;
  opacity:0.4;
  transition: linear 1s;
}

.one{
  background:url('./assets/img_mobile/1.jpg')center no-repeat;
  background-size: cover;
  height: 100vh;
  
   @media (max-width: $mediaMinWidth) {
    background: white;
  }
  @media (min-width: $mediaMidWidth) {
    background:url('./assets/img_desktop/1.jpg')center no-repeat;
  }
}

.two{
  background:url('./assets/img_mobile/2.jpg')center no-repeat;
  background-size: cover;
  height: 100vh;
  
  @media (max-width: $mediaMinWidth) {
    background: white;
  }
  @media (min-width: $mediaMidWidth) {
    background:url('./assets/img_desktop/2.jpg')center no-repeat;
  }
}

.opacity_zero{
    opacity: 0;
}
</style>
