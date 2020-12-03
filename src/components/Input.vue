<template>
<div>
    <div class="searchBar">
        <form class="form-inline justify-content-center">
            <input v-model="zip" oninput="javascript: if (this.value.length > this.maxLength) this.value = this.value.slice(0, this.maxLength);" 
        maxlength = "5" input type="number" class="form-control mb-2 mr-sm-2" id="zip" placeholder="Zip Code">
            <div class="btn-toolbar" role="toolbar" aria-label="Grouping buttons">
                <div class="btn-group mr-2" role="group" aria-label="temp">
                    <button type="button" class="btn btn-dark" :disabled="isDisabled" @click=fahrenheit()>ºF</button>
                    <button type="button" class="btn btn-dark" @click=celsius()>ºC</button>
                </div>
            </div>
        </form>
    </div>
    <Display :currentWeather="weather" :curTemp="temp" :unit="imperial" :highTemp="maxTemp" :lowTemp="minTemp" :rise="sunrise" :set="sunset"/>
</div>
</template>



<script>
import Display from './Display.vue'
import axios from 'axios'

export default {
    name: "Input",
    components: {
        Display,
    },
    data() {
        return {
            zip: 0,
            weather: '',
            temp: 0,
            maxTemp: 0,
            minTemp: 0,
            sunrise: 0,
            sunset: 0,
            imperial: true,
            search: false,
        }
    },
    mounted(){
    axios.get('https://api.openweathermap.org/data/2.5/weather?zip=65721,us&units=imperial&appid=dc86f2dcaa61375d94a561a001694478')
    .then( (response) => {
      this.weather = response.data;
      this.imperial = true;
      this.temp = response.data.main.temp.toFixed();
      this.maxTemp = response.data.main.temp_max.toFixed();
      this.minTemp = response.data.main.temp_min.toFixed();
      this.sunrise = new Date(response.data.sys.sunrise*1000).toLocaleTimeString("en-US").slice(0,4);
      this.sunset = new Date(response.data.sys.sunset*1000).toLocaleTimeString("en-US").slice(0,4);
    })
  },
    methods: {
    fahrenheit()
    {
        if (this.zip.length != 5){
            alert('Zip code must contain 5 digits');
            this.zip = 0;
        }
        else {
        axios.get('https://api.openweathermap.org/data/2.5/weather?zip=' + this.zip + ',us&units=imperial&appid=dc86f2dcaa61375d94a561a001694478')
        .then( (response) => {
            this.weather = response.data;
            this.temp = response.data.main.temp.toFixed();
            this.maxTemp = response.data.main.temp_max.toFixed();
            this.minTemp = response.data.main.temp_min.toFixed();
            this.sunrise = new Date(response.data.sys.sunrise*1000).toLocaleTimeString("en-US").slice(0,4);
            this.sunset = new Date(response.data.sys.sunset*1000).toLocaleTimeString("en-US").slice(0,4);
        });
        this.imperial = true;
    }
    },
    celsius()
    {
        if (this.zip.length != 5){
            alert('Zip code must contain 5 digits');
            this.zip = 0;
        }
        else {
        axios.get('https://api.openweathermap.org/data/2.5/weather?zip=' +this.zip+ ',us&units=metric&appid=dc86f2dcaa61375d94a561a001694478')
        .then( (response) => {
            this.weather = response.data;
            this.temp = response.data.main.temp.toFixed();
            this.maxTemp = response.data.main.temp_max.toFixed();
            this.minTemp = response.data.main.temp_min.toFixed();
            this.sunrise = new Date(response.data.sys.sunrise*1000).toLocaleTimeString("en-US").slice(0,4);
            this.sunset = new Date(response.data.sys.sunset*1000).toLocaleTimeString("en-US").slice(0,4);
        })
        this.imperial = false;
        }
    },
},
}
</script>

<style scoped>
    .searchBar
        {
            background: #000;
            color: white;
            text-align: center;
            padding: 10px;
            margin: 0px;
        }
</style>