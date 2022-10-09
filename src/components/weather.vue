<template>
    <div>
        <div class="search-box">
            <input 
            type="text" 
            class="search-bar" 
            placeholder="search..."
            v-model="query"
            @keypress="fetchWeather"
            >
        </div>

        <div class="weather-wrap" v-if="typeof weather.main != 'undefined'">

            <div class="location-box">
                <div class="location">{{ weather.name }}</div>
                <div class="date">{{ dateBuilder() }}</div>
            </div>
        
            <div class="weather-box">
                <div class="temp">{{ Math.round(weather.main.temp) }}°</div>
                <div class="weather"> {{ weather.weather[0].main }} </div>
            </div>

        </div>
        <div class="weather-wrap" v-else>
            <div class="location-box">
                <div class="location">City not found</div>
                <div class="date">{{ dateBuilder() }}</div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'app',
    data() {
        return {
            api_key: 'f114c1d8edfe049f0d1de15551609120',
            url_base: 'https://api.openweathermap.org/data/2.5/',
            query: '',
            weather: {}
        }
    },

    methods: {
        fetchWeather(e) {
            if(e.key == "Enter") {
                fetch(`${this.url_base}weather?q=${this.query}&units=metric&APPID=${this.api_key}`)
                .then(res => {
                    return res.json();
                }).then(this.setResults);
            }
        },
        setResults(results) {
            this.weather = results;
            console.log(results);
        },

        dateBuilder() {
            let d = new Date();

            let months = ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"];
            let days = ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"];

            let day = days[d.getDay()];
            let date = d.getDate();
            let month = months[d.getMonth()];
            let year = d.getFullYear();
            return `${day} ${date} ${month} ${year}`;
        }

        
    },

    setup () {
        return {}
    }
}
</script>

<style lang="css" scoped>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    user-select: none; 
}

.search-box .search-bar {
    display: block;
    widows: 100%;
    padding: 15px;
    margin: 15px 0;

    color: #8f8f8f;
    font-size: 20px;
    background-color: rgba(255, 255, 255, 0.15);
    border-radius: 12px;

    appearance: none;
    border: none;

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
    font-size: 48px;
    font-weight: 700;
    text-shadow: 0 0 32px rgba(110, 106, 106, 0.1);
}
</style>