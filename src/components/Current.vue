<template>
    <v-container class="mt-n7" v-if="weather && weather.current">
        <h2>{{weather.location.name}}, {{weather.location.region}}, {{weather.location.country}}</h2>
    <v-container class="mt-n3 ml-n1">
        <v-container class="mt-n4 ml-n4">Updated on {{weather.current.last_updated}}</v-container>
        <v-container class="mt-n2">Wind: {{weather.current.wind_kph}}</v-container>
        <v-container class="mt-n7">Humidity: {{weather.current.humidity}}</v-container>
        <v-container class="mt-n7">Gust: {{weather.current.gust_kph}}</v-container>
        <v-container class="mt-n7">Precip: {{weather.current.precip_mm}}</v-container>
        <v-container class="mt-n7">Pressure: {{weather.current.pressure_mb}}</v-container>
    </v-container>
    
        {{ weather.current.temp_c }}
    </v-container>
</template>

<script>

export default {
  props: {
    location: String,
  },
  data() {
    return {
      weather: null,
    };
  },
  watch: {
    location(loc) {
      this.weather = this.getWeather(loc);
      console.log("weather: " + this.weather);
    },
  },
  methods: {
    async getWeather(location) {
        console.log("here: ", location)
        await fetch(
            `https://api.weatherapi.com/v1/current.json?q=${location}&key=${process.env.VUE_APP_WEATHER_API_KEY}`
        ) .then((response) => response.json())
        .then((data) => {
            console.log(data)
            this.weather = data
        })
    }
  }
};
</script>
