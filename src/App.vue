<template>
  <div id="app">
    <h1> Weather </h1>
    <h2>{{ search.data }}</h2>
    <h3> {{ goGo }}</h3>
    <div class="container">
      <div class="row justify-center">
        <div class="search-box">
          <form action="#" v-on:submit.prevent="keyPress()">
            <!-- <input v-model="search.data" placeholder="Enter city to search..." v-on:change="keyPress(search.data)"> -->
            <input type="search" v-model="search.data" placeholder="-----">
            <input type="submit" v-on:click="keyPress" value="Search">
            <!-- <button v-on:click="">Search</button> -->
          </form>
        </div>
      </div>
    </div>
    <div class="container">
      <div class="row justify-center">
        <div class="weather-data">
          <div class="weather-condition">
            <span class="weather-icon">
              <img v-bind:src="weatherIcons[weatherData.currWea]" alt="weather-icon">
            </span>
            <p class="temperature">{{ weatherData.currTemp }}&deg;C</p>
          </div>
          <div class="weather-information">
            <ul class="condition-list">
              <li>{{ geo.code }}</li>
              <li>Latitude: {{ geo.posX }}</li>
              <li>Longitude: {{ geo.posY }}</li>
              <li>Condition: {{ weatherData.currWea }} </li>
              <li>Location: {{ geo.city }}</li>
              <li>Visibility: {{ weatherData.currVis }} Km</li>
              <li>Wind speed: {{ weatherData.currWind }} Km/h</li>
            </ul>
          </div>
        </div>
      </div>
    </div>
    <!--Location-->
    <div class="container">
      <div class="row justify-center">
        <div class="location">
          <p>Current location: {{ geo.city }} </p>
        </div>
      </div>
    </div>
  </div>

</template>
<script>
import myHeader from './components/Header'
import myMenu from './components/Menu'
import myContent from './components/Content'
import myFooter from './components/Footer'

export default {
  name: 'app',
  components: {
    myHeader,
    myMenu,
    myContent,
    myFooter
  },
  data () {
    return {
      search: {
        data: 'Odessa, Ukraine'
      },
      geo: {
        code: 'Odessa',
        country: 'Ukraine',
        city: 'undef',
        posX: 'undef',
        posY: 'undef'
      },
      context: {
        that: this
      },
      weatherData: {
        day: 'tgeo.item.forecast.day',
        date: 'tgeo.item.forecast.date',
        tempH: 'tgeo.item.forecast.high',
        tempL: 'tgeo.item.forecast.low',
        dataCode: 'tgeo.item.forecast.code',
        currTemp: 'fuck off',
        currVis: 'blind as ass',
        currWea: 'total shit',
        currWind: 'Not set'
      },
      weatherIcons: {
        'Partly Cloud': 'src/assets/assets/weather-icons/partly-cloudy.svg',
        'Partly Cloudy': 'src/assets/assets/weather-icons/partly-cloudy.svg',
        'Sunny': 'src/assets/assets/weather-icons/sunny.svg',
        'Breezy': 'src/assets/assets/weather-icons/partly-cloudy.svg',
        'Fair': 'src/assets/assets/weather-icons/sunny.svg',
        'Clear': 'src/assets/assets/weather-icons/sunny.svg',
        'Mostly Sunny': 'src/assets/assets/weather-icons/sunny.svg',
        'Mostly Clear': 'src/assets/assets/weather-icons/partly-cloudy.svg',
        'Cloudy': 'src/assets/assets/weather-icons/cloudy.svg',
        'Mostly Cloudy': 'src/assets/assets/weather-icons/cloudy.svg',
        'Isolated Thunderstorms': 'src/assets/assets/weather-icons/rain-mix.svg',
        'Thundershowers': 'src/assets/assets/weather-icons/rain-mix.svg',
        'Heavy Thunderstorms': 'src/assets/assets/weather-icons/rain-mix.svg',
        'PM Thunderstorms': 'src/assets/assets/weather-icons/rain-mix.svg',
        'Light Rain with Thunder': 'src/assets/assets/weather-icons/rain-mix.svg',
        'Scattered Thunderstorms': 'src/assets/assets/weather-icons/rain-mix.svg',
        'Rain': 'src/assets/assets/weather-icons/rain.svg',
        'AM Rain': 'src/assets/assets/weather-icons/rain.svg',
        'PM Rain': 'src/assets/assets/weather-icons/rain.svg',
        'Showers': 'src/assets/assets/weather-icons/hail.svg',
        'Heavy Rain': 'src/assets/assets/weather-icons/hail.svg',
        'Light Rain': 'src/assets/assets/weather-icons/rain-mix.svg',
        'AM Showers': 'src/assets/assets/weather-icons/hail.svg',
        'Scattered Showers': 'src/assets/assets/weather-icons/hail.svg',
        'PM Showers': 'src/assets/assets/weather-icons/hail.svg',
        'Rain And Snow': 'src/assets/assets/weather-icons/rain-mix.svg',
        'Snow': 'src/assets/assets/weather-icons/snow.svg'
      }
    }
  },
  methods: {
    keyPress: function () {
      console.log('You still thinking this works?')
    },
    ipApi: (sData) => {
      var xhttp
      xhttp = new XMLHttpRequest()
      xhttp.onreadystatechange = function () {
        if (this.readyState === 4 && this.status === 200) {
          let tgeo = JSON.parse(this.responseText)
          // console.log(tgeo)
          sData.code = tgeo.country_code
          sData.country = tgeo.country_name
          sData.city = tgeo.city
          sData.posX = tgeo.latitude.toString()
          sData.posY = tgeo.longitude.toString()
        }
      }
      xhttp.open('GET', 'https://freegeoip.net/json/', true)
      xhttp.send()
    },
    getYahooWeather: (pData, wData) => {
      var xhttp
      xhttp = new XMLHttpRequest()
      xhttp.onreadystatechange = function () {
        if (this.readyState === 4 && this.status === 200) {
          let tgeo = JSON.parse(this.responseText)
          console.log(tgeo)
          if (tgeo.query.results !== null) {
            wData.currVis = tgeo.query.results.channel.atmosphere.visibility.toString()
            wData.currTemp = tgeo.query.results.channel.item.condition.temp.toString()
            wData.currWea = tgeo.query.results.channel.item.condition.text.toString()
            wData.currWind = tgeo.query.results.channel.wind.speed.toString()
            // wData.date = tgeo.query.results.channel[0].item.forecast.date
            // wData.tempH = tgeo.query.results.channel[0].item.forecast.high
            // wData.tempL = tgeo.query.results.channel[0].item.forecast.low
            // wData.dataCode = tgeo.query.results.channel[0].item.forecast.code
          }
        }
      }
      xhttp.open('GET', 'https://query.yahooapis.com/v1/public/yql?q=select%20*%20from%20weather.forecast%20where%20woeid%20in%20(select%20woeid%20from%20geo.places(1)%20where%20text%3D%22' + pData.city + ',' + pData.code + "%22)and%20u%3D'c'&format=json&env=store%3A%2F%2Fdatatables.org%2Falltableswithkeys", true)
      xhttp.send()
    },
    initWeather: (go, gh) => {
      if ('geolocation' in navigator) {
        navigator.geolocation.getCurrentPosition((position) => {
          var xhttp
          xhttp = new XMLHttpRequest()
          xhttp.onreadystatechange = function () {
            if (this.readyState === 4 && this.status === 200) {
              let tgeo = JSON.parse(this.responseText)
              console.log(tgeo + 'initWeather: (go, gh)')
              console.log(JSON + 'initWeather: (go, gh)')
              gh.code = tgeo.results[1].address_components[3].short_name
              gh.country = tgeo.results[1].address_components[2].long_name
              gh.city = tgeo.city
            }
          }
          gh.posX = position.coords.latitude
          gh.posY = position.coords.longitude
          xhttp.open('GET', 'http://maps.googleapis.com/maps/api/geocode/json?latlng=' + position.coords.latitude + ',' + position.coords.longitude, true)
          xhttp.send()
        },
        go.that.ipApi(gh))
      } else {
        console.log(go.that)
        console.log(gh)
        go.that.ipApi(gh) // Alternative service find by IP
      }
    }
  },
  computed: {
    goGo: function () {
      this.search.data.toString()
      console.log(this.search.data.lenght)
      // this.search.data.split(',')
      this.geo.city = this.search.data
      this.geo.country = ', '
      this.getYahooWeather(this.geo, this.weatherData)
    }
  },
  created () {
    this.getYahooWeather(this.geo, this.weatherData)
    console.log('step 2')
    this.initWeather(this.context, this.geo)
    console.log('step 1')
  },
  beforeMount () {
  }
}
</script>

<style lang='scss' scoped>
 @import 'assets/scss/main';
 body{
   @include background;
 }
 // App
 #app {
   font-family: 'Avenir', Helvetica, Arial, sans-serif;
   -webkit-font-smoothing: antialiased;
   -moz-osx-font-smoothing: grayscale;
   text-align: center;
   color: #2c3e50;
   margin-top: 60px;
 }
 // Search box
 .search-box{
   @include shadow;
   border-radius: 20px 20px 0 0;
   height:5rem;
   background: $background_color1;
   flex-basis: 60%;
   border-bottom: 1px solid rgba(19, 20, 27, 0.24);
   input[type="search"]{
     height: 40px;
     width: 70%;
     margin-top: 20px;
     padding-left: 15px;
     @include light;
   }
   input[type="submit"]{
     height: 40px;
     width: 20%;
     @include light;
     &:hover{
       cursor: pointer;
       @include dark;
     }
   }
 }
   // Weather data
   .weather-data{
     /*padding-top: 5px;*/
     padding-bottom: 5px;
     height:13rem;
     background: $background_color1;
     flex-basis: 60%;
     border-bottom: 1px solid rgba(19, 20, 27, 0.24);
     display: flex;
     flex-direction: row;
     .weather-condition{
       margin-left: 5px;
       margin-right: 5px;
       flex-basis: 50%;
       background: $background_color2;
       @include shadow_inset;
       span.weather-icon{
         position: relative;
         img{
           padding-top: 20px;
           width: 120px;
         }
       }
       p.temperature{
         margin: 0 0 0 15px ;
         position: relative;
         color: $font_color2;
         font-size: 2rem;
       }
     }
     .weather-information{
       flex-basis: 50%;
       background: $background_color1;
       ul.condition-list{
         text-align:left;
         list-style: none;
         padding-top: 20px;
         padding-left: 60px;
         padding-right: 10px;
         li{
           color: $font_color;
         }
       }
     }
   }
   // Location
   .location{
     @include shadow;
     /*flex: 2;*/
     height:4rem;
     background: $background_color3;
     flex-basis: 60%;
     p{
       padding-top: 10px;
       color: $font_color;
       &::before{
         content: url("/src/assets/assets/other-icons/location.svg");
         position: absolute;
         width: 40px;
         height: 30px;
         margin-left: -60px;
         margin-top: -13px;
         animation: locationIcon 3s linear 2s infinite;
         @keyframes locationIcon {
           0%   {opacity: 1}
           50%  {opacity: 0.5}
         }
       }
     }
   }
</style>
