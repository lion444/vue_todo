<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>{{count}}</h2>
    <p>
      <button v-on:click="add()">add</button>
    </p>
    <p>
      <button v-on:click="changeColor()">change color</button>
    </p>
    <p>
      <input type="text" v-model="textColor" />
    </p>
    <p>
      <button v-on:click="getWeather()">check weather</button>
    </p>
    <p id="weather">
      Car color is {{car.color}}
      <br />
      Weather: {{weather}}
      <br />

      <br />
    </p>
    And has {{car.wheelCount}} wheels
  </div>
</template>

<script>
let Car = function(color, wheelCount) {
  this.color = color;
  this.wheelCount = wheelCount;
};
let blueCar = new Car("blue", 4);
export default {
  name: "HelloWorld",
  props: {
    msg: String
  },
  data: function() {
    return {
      car: blueCar,
      car2: new Car("Red", 4),
      textColor: "",
      weather: ""
    };
  },
  methods: {
    add: function() {
      blueCar.wheelCount++;
    },
    changeColor: function() {
      this.car.color = this.textColor;
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
</style>
