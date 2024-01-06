<script>

</script>

<template>
    <div class="wrapper">
        <h1 class="weather-title">Weather app</h1>
        <p class="weather-par">Find out the weather in your city</p>
        <input class="weather-input" type="text" placeholder="Enter your city">
        <button class="weather-button">Get the weather</button>
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
</style>
