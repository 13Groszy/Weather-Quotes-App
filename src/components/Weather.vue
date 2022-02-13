<template>
    <div>
        <div class="input__wrapper">
            <input v-on:keyup.enter="getWeather()" v-model="cityName" type="text" placeholder="Search for a city">
            <button @click="getWeather()" type="submit">FIND</button>
        </div>
        <div v-if="storage === 1" class="results">
            <p>Local Time: {{localTime}}</p>
            <p>Country: {{country}}</p>
            <p>Conditions: {{weather}}</p>
            <p>Temperature: {{tempC}}°C</p>
            <p>FeelsLike: {{feelsC}}°C</p>
            <p>Pressure: {{pressure}} hPa</p>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Weather',
    data(){
        return {
            cityName: '',
            locationName: '',
            localTime: '',
            country: '',
            weather: '',
            tempC: '',
            feelsC: '',
            pressure: '',
            storage: 0,
        }
    },
    methods: {
        async getWeather(){
            const url = "https://weatherapi-com.p.rapidapi.com/current.json?q=" + this.cityName;
            fetch(url, {
	"method": "GET",
	"headers": {
		"x-rapidapi-host": "weatherapi-com.p.rapidapi.com",
		"x-rapidapi-key": "e33e7e2ed0msh892b2efa6865100p1017fcjsn1fc34ba00b5c"
	},
})
.then(response => response.json())
.then(response => {
    this.locationName = response.location.name
    this.country = response.location.country
    this.localTime = response.location.localtime
    this.weather = response.current.condition.text
    this.tempC = response.current.temp_c
    this.feelsC = response.current.feelslike_c
    this.pressure = response.current.pressure_mb
    this.storage = 1;
    this.$emit('pass-city-name', this.locationName.toUpperCase())
})
.catch(err => {
	console.error(err);
    this.storage--;
    this.$emit('pass-city-name', '')
    alert('Type a correct city name')
})
}
}
}
</script>
<style lang="scss" scoped>
.input__wrapper{
margin-top: 1rem;
}
input{
    background: transparent;
    border: none;
    border-bottom: 1px solid grey;
    color:#000;
    width:8rem;
    &::placeholder{
        color:#000;
    }
}
button{
    background-color: transparent;
    border:0;
    padding:0.5rem;
    border-radius: 5px;
}
</style>