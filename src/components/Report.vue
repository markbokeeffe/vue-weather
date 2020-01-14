<template>
  <div>
    <div class="header">
      Weather Forecast
    </div>
    <div class="selection">
      <SelectDropdown label="Select a location" v-bind:model="this.location" v-on:updateLocation="updateLocation($event)" v-bind:options="this.locations"/>
    </div>
    <TableBasic v-bind:table="this.weather"/>
 </div>
</template>

<script>
import axios from 'axios';
import { API_KEY, locations } from '../constants';
import SelectDropdown from '../components/SelectDropdown.vue';
import TableBasic from '../components/TableBasic.vue';

export default {
  name: 'Report',
  props: {
    title: String
  },
  components: {
    SelectDropdown,
    TableBasic
  },
  data () {
    return {
      weather: null,
      locations,
      location: 'Dublin'
    }
  },
  methods: {
    getWeather: function() {
      axios
        .get(`https://api.weatherbit.io/v2.0/current?city=${this.location},IE&key=${API_KEY}`)
        .then(response => (this.weather = this.formatWeatherData(response.data.data)))
    },
    updateLocation: function(e) {
      this.location = e;
      this.getWeather();
    },
    formatWeatherData: function(data) {
      const columns = ['Sunrise', 'Sunset', 'Clouds', 'Rain', 'Temperature'];
      const { sunrise, sunset, clouds, precip, app_temp } = data[0];
      const rows = [ sunrise, sunset, clouds, precip, app_temp ];
      return {
        columns,
        rows
      }
    }
  },
  mounted () {
    this.getWeather();
  }
}
</script>

<style scoped>
.header{
    background-color:aquamarine;
    color:darkslategrey;
    display: flex;
    justify-content: center;
    height: 140px;
    align-content: center;
    align-items: center;
    font-size: 40px;
    font-weight: bold;
}
  .selection {
    background-color:#fff;
    color:darkslategrey;
    padding: 20px 0px;
  }
</style>
