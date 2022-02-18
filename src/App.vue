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
      let bg = document.querySelector('.bg__img');
      setInterval(function(){
        if (bg.classList.contains("one")) {
          bg.classList.add('two');
          bg.classList.remove('one');
        }
        else{
          bg.classList.add('one');
          bg.classList.remove('two');
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
  height: 100vh;
  z-index:-2;
  opacity:0.4;
  transition: linear 1s;
}
.one{
  background:url('./assets/img_mobile/1.jpg')center no-repeat;
  background-size: cover;
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
  @media (max-width: $mediaMinWidth) {
    background: white;
  }
  @media (min-width: $mediaMidWidth) {
    background:url('./assets/img_desktop/2.jpg')center no-repeat;
  }
  
}
</style>
