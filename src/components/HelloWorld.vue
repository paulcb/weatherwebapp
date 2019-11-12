<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>{{lat}}, {{lon}}</p>
    <p>{{temp}}</p>
    <ol>
      <li v-for="(value, name) in daily.data" v-bind:key="name">
        <p>{{day[new Date( value.temperatureHighTime * 1000).getDay()]}}</p>
        <p>High {{ value.temperatureHigh }}</p>
        <p>Low {{ value.temperatureLow }}</p>
      </li>
    </ol>
    <line-chart :chartdata="chartData" :options="chartOptions" />
    <p>bottom</p>
  </div>
</template>

<script>
import weather from "../assets/weather.json"
import LineChart from './LineChart.vue'

export default {
  components: {
    LineChart
  },
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data: function() {
    return {
      daily: weather.daily,
      temp: weather.currently.apparentTemperature,
      lat: weather.latitude,
      lon: weather.longitude,
      day: ["Sun", "Mon", "Tues", "Wed", "Thurs", "Fri", "Sat"]
    };
    // return { daily: weather.daily,
    //  cur: weather.current.apparentTemperature,
    //  lat: weather.latitude,
    //  lon: weather.longitude};
  }
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
</style>
