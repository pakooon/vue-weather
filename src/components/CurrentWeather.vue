<template>
  <div>
    <div class="location">{{location}}</div>
    <div class="weather">{{weather}}</div>
    <div class="temp">{{temp}}C</div>
  </div>
</template>

<script>
export default {
  name: 'current-weather',
  data () {
    return {
      location: 'Seoul',
      weather: 'Rain',
      temp: '30C',
      lat: 37.566535,
      lon: 126.977969
    }
  },
  methods: {
    setCoordinate (coordinate) {
      this.lat = coordinate.lat
      this.lon = coordinate.lng
      this.axios.get('https://api.openweathermap.org/data/2.5/weather', {
        params: {
          lat: this.lat,
          lon: this.lon,
          APPID: '4364fd05ab86fe17f573ee4bafe99777'
        }
      })
      .then(response => {
        let data = response.data
        console.log(data)
        this.location = data.name
        this.weather = data.weather[0].main
        this.temp = (data.main.temp - 273.15).toFixed(0)
      })
    }
  },
  mounted () {
    this.$bus.$on('sendCoordinate', this.setCoordinate)
  }
}
</script>

<style scoped>
.location {
  text-align: center;
  font-size: 40pt;
  color: white;
}
.weather {
  text-align: center;
  font-size: 20pt;
  color: white;
}
.temp {
  text-align: center;
  font-size: 50pt;
  color: white;
}
</style>