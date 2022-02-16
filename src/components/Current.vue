<template>
  <div>
    The Location is: {{ location }}
    <p v-if="weather && weather.current">{{ weather.current.temp_c }}</p>
  </div>
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
    //   console.log(this.weather.current);
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
