<template>
    <div class="container">
        <div class="jumbotron jumbotron-fluid">
            <div class="container">
                <h1 class="display-4">{{currentWeather.name}}</h1>
                <h2>Current Conditions</h2>
                <p class="lead"><strong>Temperature</strong></p>
                <p>Current Temp: {{curTemp}}<span v-if="unit===false">°C</span><span v-else>°F</span></p>
                <p>
                {{currentWeather.weather[0].main}} - {{currentWeather.weather[0].description}}<img :src="'http://openweathermap.org/img/wn/' + currentWeather.weather[0].icon + '@2x.png'"></p>
                <h2>Today's Forcast</h2>
                <p>High Temp: {{highTemp}}<span v-if="unit===false">°C</span><span v-else>°F</span></p>
                <p>Low Temp: {{lowTemp}}<span v-if="unit===false">°C</span><span v-else>°F</span></p>
                <p>Sunrise: {{rise}} A.M.</p>
                <p>Sunset: {{set}} P.M.</p>
            </div>
        </div>
    </div>
</template>

<script>

export default {
    name: "Display",
    props: ['currentWeather', 'curTemp', 'unit', 'highTemp', 'lowTemp', 'rise', 'set']
}
</script>