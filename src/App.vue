<template>
  <div id="app">
    <div id="information">
      <div id="current-weather">
        <current-weather/>
      </div>

      <hr>

      <div id="forecast">
        <forecast></forecast>
      </div>
    </div>

    <div id="map"> 
      <google-map></google-map>
    </div>
    
  </div>
</template>

<script>
import CurrentWeather from './components/CurrentWeather'
import GoogleMap from '@/components/GoogleMap'
import Forecast from '@/components/Forecast'

export default {
  name: 'app',
  components: {
    CurrentWeather,
    GoogleMap,
    Forecast
  }
}
</script>

<style>
body {
  background-color: #fafafa;
}
#app {
  position: absolute;
  top: 50%;
  left: 50%;
  width: 1000px;
  height: 600px;
  margin-top: -300px;
  margin-left: -500px;
  border-radius: 3px;
  background-color: #444;
  box-shadow: 0px 2px 2px 2px rgba(0, 0, 0, 0.3);
}
#app:after {
  content: '';
  display: block;
  clear: both;
}
#app > #information {
  float: left;
  width: 600px;

}
#app > #information > #current-weather {
  /*margin-top: 20px;*/
  height: 200px;
}
hr {
  width: 80%;
  margin: 50px auto;
  border: none;
  border-top: 1px solid white;
}
#app > #information > #forecast {
  height: 400px;
}
#app > #map {
  float: right;
  width: 400px;
  height: 600px;
}
</style>
