<template>
    <div class="box">
      <h1>{{messageBuilder()}}</h1>
        <input v-model="query
        " type="text"
         placeholder="Search by location..."
         @keypress="fetchWeather"
         />
         <div class="weather-content" v-if="weather.main != undefined">
        <h2>{{weather.name}}, {{weather.sys.country}}</h2>
        <p>{{dateBuilder()}}</p>
        <span>{{Math.round(weather.main.temp)}}ºc</span>
        <h3>{{weather.weather[0].main}}</h3>
        <p>{{weather.weather[0].description}}</p>
        <!-- import icons -->
		<IconsWeather :currentWeather="currentWeather"/>
         </div>
    </div>
</template>

<script>
import IconsWeather from './IconsWeather.vue'

export default {
    name: 'BoxContent',
	components: {
		IconsWeather,
	},

	data(){
		return{
			//api weather
			api_key: '8ee5579196e0ebc8f2a28c5e7ea6a397',
			url_base: 'https://api.openweathermap.org/data/2.5/',
			query: '',
      hours: '',
			weather: {},
      currentWeather: ''
		}
	}, 
	methods: {  
		fetchWeather(e){
		if(e.key == "Enter"){
			fetch(`${this.url_base}weather?q=${this.query}&units=metric&APPID=${this.api_key}`)
			.then(res => {
			return res.json()
			}).then(this.setResults)
		}
    },
    setResults(results){
      this.weather = results
      // console.log(this.weather)
      this.currentWeather = this.weather.weather[0].main
      this.query = '';
    },

    // building data
    dateBuilder(){
      let date = new Date();
      let months = ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"]
      let days = ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"]

      let dayOfWeek = days[date.getDay()]
      let day = date.getDate()
      let month = months[date.getMonth()]
      let year = date.getFullYear()

      return `${dayOfWeek} ${day} ${month} ${year}`

    },

    // building h1 message
    messageBuilder(){
      this.hours = new Date().getHours()
      
      if(this.hours >= 5 && this.hours < 12){
        return 'Good Morning'
      }else if(this.hours >= 12 && this.hours < 18){
        return 'Good Afternoon'
      }else{
        return 'Good Evening'
      }
    }
  },
}

</script>

<style>
 @import '/src/assets/icon.css';

</style>