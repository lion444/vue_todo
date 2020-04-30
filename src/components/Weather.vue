<template>
  <div class="hello">
    <div id="divider">WEATHER</div>
    <p>
      <input type="text" v-model="city" />
    </p>
    <p>
      <button v-on:click="changeCity()">changeCity</button>
    </p>
    <p id="weather">{{weather.city}} is {{weather.temp}} and it is {{weather.raining}}</p>
  </div>
</template>

<script>
let Weather = function(city, temp, raining) {
  this.city = city;
  this.temp = temp;
  this.raining = raining;
};

export default {
  name: "Weather",
  props: {},
  data: function() {
    return {
      weather: new Weather("60050", 55, false),
      city: ""
    };
  },
  methods: {
    changeCity: function() {
      this.weather.city = this.city;
    },

    getWeather: function() {
      this.weather = getWeatherFromAPI("hot");
    }
  }
};

let getWeatherFromAPI = w => {
  return w;
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
#weather {
  color: aqua;
  background-color: black;

  margin: 40px 0 0;
}
#divider {
  background-color: blue;
  color: white;
}
</style>
