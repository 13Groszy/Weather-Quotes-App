<template>
    <div>
        <h2>Enter a city name to find out the weather forecast</h2>
        <div class="input__wrapper">
            <input v-on:keyup.enter="getWeather()" v-model="cityName" type="text" placeholder="Search for a city">
            <button @click="getWeather()" type="submit">Search</button>
        </div>
        <div v-if="storage === 1" class="results">
            <p>Local Time: <span>{{localTime}}</span></p>
            <p>Country: <span>{{country}}</span></p>
            <p>Conditions: <span>{{weather}}</span></p>
            <p>Temperature: <span>{{tempC}}°C</span></p>
            <p>FeelsLike: <span>{{feelsC}}°C</span></p>
            <p>Pressure: <span>{{pressure}} hPa</span></p>
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
    input{
        background: transparent;
        border: none;
        border-bottom: 1px solid grey;
        color:#000;
        width:15rem;
        font-size:1rem;
        margin-right: 2vw;

        &::placeholder{
            color:rgb(61, 61, 61);
        }

        &:focus{
        outline: none;
        }
    }

    button{
        background-color: rgb(8, 151, 233);
        border:0;
        border-radius: 5px;
        padding:0.5rem;
        margin-top:1rem;
    }
}
.results{
    margin-top:5vh;

    p{
        margin:1rem;
        font-size: 1.5rem;
        font-weight: bold;
    }
    span{
        font-size:1.2rem;
        font-weight: normal;
    }
}
</style>
