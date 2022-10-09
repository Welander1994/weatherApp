<script setup>
import { ref } from 'vue';
import Rain from './rain.vue';

               const api_key = 'f114c1d8edfe049f0d1de15551609120';
               const url_base = 'https://api.openweathermap.org/data/2.5/';
               let query = ref(''); 
               let weather = ref({});
               var itsRaining = ref(false);
               
        
             async function fetchWeather() {

                    await fetch(`${url_base}weather?q=${query.value}&units=metric&APPID=${api_key}`)
                    .then(res => {
                        return res.json();
                    })
                    .then(setResults);
                
            };

            function setResults(results) {
                weather.value = results;     
                console.log(results); 
                if(results.weather[0].main == 'Rain') {
                    itsRaining.value = true;
                    
                }       
            };

 
    
            function dateBuilder() {
                let d = new Date();
    
                let months = ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"];
                let days = ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"];
    
                let day = days[d.getDay()];
                let date = d.getDate();
                let month = months[d.getMonth()];
                let year = d.getFullYear();
                return `${day} ${date} ${month} ${year}`;
            }
    
            
            
            

    </script>

<template>
    <div>
        <div class="search-box">
            <input 
            type="text" 
            class="search-bar" 
            placeholder="search..."
            v-model="query"
            @keydown.enter.prevent="fetchWeather"
            
            >
            <span class="material-symbols-outlined" @click="fetchWeather">search</span>
        </div>
        

        <div class="weather-wrap" v-if="typeof weather.main != 'undefined' ">

            <div class="location-box">
                <div class="location">{{ weather.name }}</div>
                <div class="date">{{ dateBuilder() }}</div>
            </div>
        

            <div class="weather-box">
                <div class="temp">{{ Math.round(weather.main.temp) }}°</div>
                <div class="weather"> {{ weather.weather[0].description }}</div>
                <div class="wind">
                    <span v-if="weather.wind.speed > 5" class="material-symbols-outlined"> air </span>
                    <span v-if="weather.wind.speed < 5" class="material-symbols-outlined"> airware </span>
                    {{ weather.wind.speed }}  
                </div>
            </div>           
        </div>
        <div class="weather-wrap" v-else>
                <div class="location-box">
                <div class="date">{{ dateBuilder() }}</div>
            </div>
        </div>
        <div v-if="itsRaining">
            <rain />    
        </div>
    </div>
</template>

<style lang="css" scoped>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    user-select: none; 
}



.search-box {
    display: flex;
    align-items: center;
}

.search-box span {
    font-size: 2rem;
    padding-left: 2vw;
}

.search-box .search-bar {
    display: block;
    max-width: 90%;
    padding: 15px;
    margin: 15px auto;
    
    
    color:  #181818;
    font-size: 20px;
    background-color: rgba(255, 255, 255, 0.25);
    border-radius: 12px;

    appearance: none;
    border: 1px solid #181818 ;

    box-shadow: 0 0 16px rgba(110, 106, 106, 0.25);
    transition: .5s ease-in-out;
}

.search-box .search-bar:focus {
    box-shadow: 0 0 32px rgba(110, 106, 106, 0.25);
    color: #fff;
    border: none;
    outline: none;
}


.location-box .location {
    color: #fff;
    font-size: 32px;
    font-weight: 500;
    text-align: center;
    text-shadow: 1px 3px rgba(0, 0, 0, 0.25);
    
}

.location-box .date {
    color: #fff;
    font-size: 20px;
    font-weight: 300;
    text-align: center;
    text-shadow: 1px 3px rgba(0, 0, 0, 0.25);
    font-style: italic;
}

.weather-box {
    text-align: center;
    padding: 10px 25px;
    
}

.weather-box .temp {
    display: inline-block;
    padding: 10px 25px;
    color: #fff;
    font-size: 102px;
    font-weight: 700;
    text-shadow: 0 0 32px rgba(110, 106, 106, 0.1);
    
}

.weather-box .weather {
    color: #fff;
    font-size: 32px;
    font-weight: 700;
    text-transform: capitalize;
    text-shadow: 0 0 32px rgba(110, 106, 106, 0.1);
}

.weather-box .wind {
    color: #fff;
    font-size: 30px;
    font-weight: 300;
    text-shadow: 1px 3px rgb(0 0 0 / 25%);
    font-style: italic;
}

.weather-box .wind span{
    font-size: 30px;
    transform: rotate(-10deg);
}




</style>