<template>
    <div>
        <h1>CHECK WEATHER</h1>
        <input v-model="cityName" type="text">
        <button @click="getWeather()" type="submit">CHECK</button>
        <div class="results">
            <p class="cityName">{{name}}</p>
            <p class="localTime">{{localTime}}</p>
            <p class="region">{{country}}</p>
            <p>Weather: {{weather}}</p>
            <p>Temperature: {{tempC}} *C</p>
            <p>FeelsLike: {{feelsC}} *C</p>
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
            name: '',
            localTime: '',
            country: '',
            weather: '',
            tempC: '',
            feelsC: '',
            pressure: '',
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
	}
})
.then(response => response.json())
.then(response => {
    this.name = response.location.name
    this.country = response.location.country
    this.localTime = response.location.localtime
    this.weather = response.current.condition.text
    this.tempC = response.current.temp_c
    this.feelsC = response.current.feelslike_c
    this.pressure = response.current.pressure_mb
    console.log(response.current)
})
.catch(err => {
	console.error(err);
})
}
}
}
</script>