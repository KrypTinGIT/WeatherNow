<template>
<div id="description">
<h1>WeatherNow</h1>
<p>Informieren Sie sich mit der WeatherNow schnell und einfach über das Wetter auf der ganzen Welt. Sie erhalten auch eine Wettervorhersage für die nächsten 4 Tage. Die Daten werden alle 10 Minuten aktualisiert. Geben Sie Ihren gesuchten Ort in das untenstehende Eingabefeld ein. Ihr WeatherNow-Team!</p>
</div>
<div id="input-panel">
<input id="input" type="text" placeholder="Ort" v-model="myLocation" />
<button id="submit" v-on:click="searchWeather">🔎</button>
</div>
<div v-if="this.validRequest">
    <div id="weatherBox" v-if="this.dailyWeatherData.validData">
    <div id="background-panel">
    <div id="foreground-panel">
        <table id="weather-content">
            <tr>
                <td id="table-left"><DailyWeatherOverview v-bind:weather="dailyWeatherData" />
                <DailyWeatherDescription v-bind:weather="dailyWeatherData" /></td>
                <td id="table-right"><DailyWeatherDetails v-bind:weather="dailyWeatherData" /></td>
            </tr>
            <tr>
                <WeatherForecast v-bind:forecast="forecastWatherData" />
            </tr>
        </table>
    </div>
    </div>
    </div>
</div>
<div v-else>
    <h2 id="error">Ooops, da ist etwas schief gelaufen</h2>
</div>
</template>

<script>

import DailyWeatherOverview from "./DailyWeatherOverview.vue";
import DailyWeatherDescription from "./DailyWeatherDescription.vue";
import DailyWeatherDetails from "./DailyWeatherDetails.vue";
import WeatherForecast from "./WeatherForecast.vue";
import config from '../config.js'

export default {
    name: 'ApiRead',
    methods: {
        searchWeather() {
            let url = 'https://api.openweathermap.org/data/2.5/weather?units=metric&lang=de&q=' + this.myLocation + '&appid=' + config.weatherAPIKey;
            console.log(url);
            fetch( url )
                .then ( async response => await response.json() )
                .then ( (responseJSON) => this.storeData(responseJSON))
                .catch ( error => alert(error) )
        },
        getForecast(latitude, longitude) {
            let url = 'https://api.openweathermap.org/data/2.5/onecall?lat=' + latitude + '&lon=' + longitude + '&units=metric&lang=de&exclude=current,hourly,minutely&appid=' + config.weatherAPIKey;
            console.log(url);
            fetch( url )
                .then ( async response => await response.json() )
                .then ( (responseJSON) => this.storeForecast(responseJSON))
                .catch ( error => alert(error) )
        },
        storeData: function(currentWeather) {
            try {
            this.validRequest = true;
            this.dailyWeatherData.id = currentWeather.name;
            this.dailyWeatherData.temp = currentWeather.main.temp;
            this.dailyWeatherData.feelslike = currentWeather.main.feels_like;
            this.dailyWeatherData.description = currentWeather.weather[0].description;
            this.dailyWeatherData.icon = currentWeather.weather[0].icon;
            this.dailyWeatherData.humidity = currentWeather.main.humidity;
            this.dailyWeatherData.windSpeed = currentWeather.wind.speed;
            this.dailyWeatherData.windDirection = currentWeather.wind.deg;
            this.dailyWeatherData.visibility = currentWeather.visibility;
            this.dailyWeatherData.lat = currentWeather.coord.lat; 
            this.dailyWeatherData.lon = currentWeather.coord.lon;
            this.dailyWeatherData.validData = true;
            this.getForecast(this.dailyWeatherData.lat, this.dailyWeatherData.lon);
            } catch (e) {            
                this.validRequest = false; // Api Error
            }
        },
        storeForecast: function(dataForecast) {
            console.log(dataForecast.timezone);
            this.clearForecastData();
            for (let i = 1; i <= 4; i++) {
                this.addForecastDay(dataForecast.daily[i].dt,
                                    dataForecast.daily[i].temp.day,
                                    dataForecast.daily[i].weather[0].icon,
                                    dataForecast.daily[i].weather[0].description);
            }
            console.log(this.forecastWatherData);
        },
        addForecastDay(newDay, newTemperature, newIcon, newDescription) {
            this.forecastWatherData.push({
                timestamp: newDay,
                temperature: newTemperature,
                icon: newIcon,
                description: newDescription
            });
        },
        clearForecastData() {
            this.forecastWatherData = [];
        },
    },
    data: () => ({
        dailyWeatherData: {
            id: String,
            temp: Number,
            feelslike: Number,
            description: String,
            icon: String,
            humidity: Number,
            windSpeed: Number,
            windDirection: Number,
            visibility: Number,
            lat: Number,
            lon: Number,
            validData: false,
        },
        forecastWatherData: [
            {   timestamp: Number,
                temperature: Number,
                description: String
            }
        ],
        validRequest: true,
    }),
    props: {

    },
    components: {
    DailyWeatherOverview,
    DailyWeatherDetails,
    DailyWeatherDescription,
    WeatherForecast,
  },
};
</script>

<style lang="scss">
@import '@/assets/_shared.scss';

    *{
        color: $text-color;
    }
    
    #description {
        height: 12em;
        text-align: center;
        margin-left: 23em;
        margin-right: 23em;
        margin-top: 5em;
        
        h1{
            color: $main-color;
            font-size: 3em;
        }

        p{
            color: $text-color;
        }
    }

    #input-panel{
        text-align: center;
        
        #input{
            background-color: $background-color;
            border: none;
            border-radius: 2em;
            height: 2em;
            width: 20em;
            color: $highlight-color;
            padding: 0.5em 0.55em;
            font-size: 1em;
        }

        #submit{
            margin-left: 1em;
            font-size: 2em;
            border: none;
            color: none;
            padding: 0.5em;
            text-align: center;
            text-decoration: $highlight-color;
            display: inline-block;
            cursor: pointer;
            border-radius: 2em;
        }
    }

    #background-panel{
        background-color: $light-background-color;
        margin-top: 5em;
        height: 40em;
    }

    #foreground-panel{
        background-color: $highlight-color;
        display: inline-block;
        text-align: center;
        height: 30em;
        width: 40em;
        margin-left: 25em;
        margin-top: 5em;
    }

    #weather-content{
        text-align: left;
    }

    #table-left{
        padding-left: 2em;
    }

    #table-right{
        padding-right: 2em;
    }

    #error{
        padding-top: 1em;
        padding-right: 3em;
        text-align: center;
        color: $main-color;
        font-size: 2em;
    }
</style>