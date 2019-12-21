<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>Location {{lat}}, {{lon}}</p>
    <p>Currently: {{temp}} f</p>
    <ol>
      <li>
        <p>Day:</p>
        <p>High:</p>
        <p>Low:</p>
      </li>
      <li v-for="(value, name) in daily.data" v-bind:key="name">
        <p>{{day[new Date( value.temperatureHighTime * 1000).getDay()]}}</p>
        <p>{{ value.temperatureHigh }}</p>
        <p>{{ value.temperatureLow }}</p>
      </li>
    </ol>
    <!-- <LineChart :chartdata="chartData" :options="chartOptions" /> -->
    <simple-line-chart :chart-data="datacollection" />
    <p>bottom</p>
  </div>
</template>

<script>
import weather from "../assets/weather.json"
// import LineChart from './LineChart.vue'
import SimpleLineChart from './SimpleLineChart.vue'

export default {
  components: {
    // LineChart
    SimpleLineChart,
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
