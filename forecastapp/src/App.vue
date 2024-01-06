//https://api.openweathermap.org/data/2.5/weather?q=Moscow&units=metric&appid=72e677bee4db5b6fe237cbe67e2fb8f2

<script>
import axios from 'axios'

    export default {
        data() {
            return {
                city: "",
                error: "",
                info: null
            }
        },
        computed: {
            cityName() {
                return "«" + this.city + "»"
            }
        },
        methods: {
            getWeather() {
                if(this.city.trim().length < 2) {
                    this.error = "Write a name of the city more than one symbol!"
                    return false
                }
                this.error = ""

                axios.get(`https://api.openweathermap.org/data/2.5/weather?q=${ this.city }&units=metric&appid=72e677bee4db5b6fe237cbe67e2fb8f2`)
                    .then(res => (this.info = res))
            }
        }
    }
</script>

<template>
    <div class="wrapper">
        <h1 class="weather-title">Weather app </h1>
        <p class="weather-par">Find out the weather in {{ city == "" ? "your city": cityName}}</p>
        <input class="weather-input" v-model="city" type="text" placeholder="Enter your city">
        <button class="weather-button" v-if="city != ''" @click="getWeather()">Get the weather</button>
        <button class="weather-button" disabled v-else="city != ''">Enter your city</button>
        <p class="error">{{ error }}</p>

        <p v-show="info != null">{{ info }}</p>
    </div>
</template>

<style scoped>
.wrapper {
    width: 800px;
    height: 400px;
    border-radius: 50px;
    padding: 50px 20px 20px 20px;
    background: #1f0f24;
    text-align: center;
    color: #fff;
}
.weather-title {
    margin-bottom: 20px;
}
.weather-par {
    margin-bottom: 20px;
}
.weather-input {
    margin-bottom: 20px;
    background: transparent;
    border: 0;
    border-bottom: 2px solid #110813;
    color: #fcfcfc;
    font-size: 14px;
    padding: 5px 8px;
    outline: none;
    margin-right: 20px;
}
.weather-input:focus {
    border-bottom-color: #6e2d7d;
}
.weather-button {
    background: #e3bc4b;
    color: #261a1a;
    border-radius: 10px;
    border: 2px solid #b99935;
    padding: 10px 15px;
    cursor: pointer;
    transition: transform .5s ease;  
}
.weather-button:hover {
    transform: scale(1.05) translateY(-1.5px);
}
.weather-button:disabled {
    background: #775f1a;
    cursor: not-allowed;
    color: #aeaec9;
    font-size: 12px;
    font-weight: 600;
    letter-spacing: .5px;
}

.error {
    color: #dc1010a1;
    font-size: 20px;
}
</style>
