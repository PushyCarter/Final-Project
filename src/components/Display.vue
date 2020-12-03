<!--
    Name: Michael Carter
    File: Display.vue
    Description: Called the object data to provide the information and provided if statements for the specific unit of measurement.
-->
<template>
    <div class="container padding">
        <div class="jumbotron jumbotron-fluid">
            <div class="container">
                <h1 class="display-4">{{currentWeather.name}}</h1>
                <div class="row">
                    <div class="col">
                        <h2>Current Conditions</h2>
                        <p class="lead"><strong>Temperature</strong></p>
                        <p>Current Temp: {{curTemp}}<span v-if="unit===false">°C</span><span v-else>°F</span></p>
                        <p>{{currentWeather.weather[0].main}}<br/>
                        <img :src="'http://openweathermap.org/img/wn/' + currentWeather.weather[0].icon + '@2x.png'"></p>
                    </div>
                    <div class="col">
                        <h2>Today's Forcast</h2>
                        <p>High Temp: {{highTemp}}<span v-if="unit===false">°C</span><span v-else>°F</span></p>
                        <p>Low Temp: {{lowTemp}}<span v-if="unit===false">°C</span><span v-else>°F</span></p>
                        <p>Sunrise: {{rise}} A.M.</p>
                        <p>Sunset: {{set}} P.M.</p>
                    </div>
                </div>
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

<style scoped>
.padding {
    padding: 40px;
}
img {
    width: 100px;
    -webkit-filter: drop-shadow(5px 5px 5px 5px #000000);
    filter: drop-shadow(5px 5px 5px 5px #000000);
}
</style>