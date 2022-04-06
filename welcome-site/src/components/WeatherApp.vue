<template>
  <div class="container" v-if="obj" @load="test()" :style="back">
    <div class="holder">
      <table class="small">
        <tr>
          <th class="tablesmall">{{ Day }}.{{ Month }}.{{ Year }}</th>
          <th class="tablesmall">{{obj.weather[0].main}}</th>
        </tr>
        <tr>
          <th class="tablebig">{{ wea1.temp }}°C</th>
          <th class="tablebig"><!--<img :src="ikona" v-if="ikona"/>-->{{obj.sys.country}}</th>
        </tr>
      </table>
      <table class="big">
        <tr>
          <th class="tablelong">  {{obj.name}}</th>
          <th class="tablelong">Wind: {{obj.wind.speed}} km/h {{windDir}}</th>
        </tr>
        <tr>
          <th class="tablelong">Pressure: {{obj.main.pressure}} bar</th>
          <th class="tablelong">Humidity: {{obj.main.humidity}} %</th>
        </tr>
      </table>
    </div>
    <div class="image">
    </div>
  </div>
  
</template>

<script>
//import * as locationService from '../services/location'
//import * as Vue from 'vue'
//import axios from 'axios'
//import VueAxios from 'vue-axios'

export default {
  data() {
    return {
      address: null,
      lo: null,
      la: null,
      myData: null,
      wea1: [],
      info: [],
      currentDate: [],
      Day: null,
      Month: null,
      Year: null,
      Hour: null,
      Minute: null,
      ikona: null,
      obj: null,
      back: '',
      windDeg: null,
      windDir: null,
      unix_timestamp: null,
      date: null
    };
  },

  mounted() {
    console.log('Getting location...')
    navigator.geolocation.getCurrentPosition(  
      (postition) => {
        this.la = postition.coords.latitude;
        this.lo = postition.coords.longitude;
        console.log('Location aquired!')
        this.getData();
        console.log('Weather data aquired!')
      },
      (error) => {
        console.log(error.message);
      }
    )
    if(this.obj) {
      this.test()
    } else {console.log('Could not load icon in time, trying again')}
      this.getTime()

  },
  beforeUpdate() {
    this.test()
    this.calcWind()
    console.log('Everything has been displayed!')
  },
  methods: {
    getData() {
      console.log('Loading weather data...')
      this.myData =
        "https://api.openweathermap.org/data/2.5/weather?lat=" +
        //'38.895' +
        this.la +
        "&lon=" +
        //'-77.0366' +
        this.lo +
        "&appid=027ee07fafd9a678d925c3a9220c1289&units=metric";
       // https://pro.openweathermap.org/data/2.5/forecast/hourly?lat=51.1169023&lon=51.1169023&appid=027ee07fafd9a678d925c3a9220c1289&units=metric
        console.log(this.myData)
      fetch(this.myData)
        .then((res) => res.json())
        .then((data) => {
        this.wea1 = data.main;
        this.obj=data;
        });
      fetch(this.myData)
        .then((res) => res.json())
        .then((data) => (this.info = data.weather))
        .catch((err) => console.log(err.message));
        
        
    },
    getTime() {
      console.log('Importing time settings...')
      this.currentDate = new Date();
      this.Day = this.currentDate.getDate();

      this.Month = this.currentDate.getMonth() + 1;
      if (this.Month < 10) {this.Month = '0' + this.Month}
      this.Year = this.currentDate.getFullYear();
      console.log('Time settings imported!')
    },
    test() {
    console.log('Displaying icon...')
    this.ikona = '/nw/' + this.obj.weather[0].icon + '.png'
    this.back = 'background-image: url("/nw/img/' + this.obj.weather[0].icon + '.webp");'
    console.log(this.back)

    console.log('Icon displayed!')
    },
    calcWind() {
      this.windDeg=this.obj.wind.deg
      if (this.windDeg < 23 ) {this.windDir = 'N'}
      else if (this.windDeg < 68) {this.windDir = 'NE'}
      else if (this.windDeg < 114) {this.windDir = 'E'}
      else if (this.windDeg < 165) {this.windDir = 'SE'}
      else if (this.windDeg < 224) {this.windDir = 'S'}
      else if (this.windDeg < 248) {this.windDir = 'SW'}
      else if (this.windDeg < 293) {this.windDir = 'W'}
      else if (this.windDeg < 238) {this.windDir = 'NW'}
      else if (this.windDeg < 380) {this.windDir = 'N'}
    }

  }
}
</script>

<style>
.tablelong {
  color: white;
  height: 45%;
  width: 45%;
}
body {
  padding: 0px;
  margin: 0px;
}
th {
  border: none;
  padding: 0;
  margin: 0;
}
.container {

  -webkit-touch-callout: none; /* iOS Safari                           */
  -webkit-user-select: none; /* Safari                               */
  -khtml-user-select: none; /* Konqueror HTML                       */
  -moz-user-select: none; /* Firefox w przeszłości (stare wersje) */
  -ms-user-select: none; /* Internet Explorer (>=10) / Edge      */
  user-select: none;
  /* background:url('nw/img/mist.webp');*/
  justify-content: center;
  margin: auto;
  text-shadow: 3px 3px black;
  background-repeat: no-repeat;
  background-size: 100% 100%;
}
.holder {
  width: 100%;
  height: 35%;
  display: flex;
  justify-content: space-around;
}
/*.imgHolder {
  height: %;
  width: 95%;
  justify-content: space-around;
}*/
.small {
  width: 35%;
  height: 100%;
 /* border: red solid 2px;
  background-color: brown; */
  border-radius: 20px;
  margin: 5px;
  justify-content: center;
  color: white;
}
.big {
  font-size: 20px;
  width: 57.5%;
  height: 100%;
  /*border: rgb(0, 26, 255) solid 2px;
  background-color: green;*/
  border-radius: 20px;
  margin: 5px;
}
.image {
  border-radius: 10px;
  margin: 5px;
  margin-right: 10px;
  margin-left: 10px;
  margin-top: 20px;
  margin-bottom: 10px;
  width: 96.5%;
  height: 54%;
}
/*.insidesmall {
  width: 80%;
  height: 80%;
  background-color: magenta;
}*/
.tablebig {
  width: 45%;
  height: 50%;
  font-size: 42px;
  font-weight: bold;
}
.tablesmall {
  font-size: 24px;
  height: 40%;
  width: 45%;
  bottom: 0;
}
.pic {
  opacity: 30%;
  border-radius: 20px;
  height: 100%;
  width: 100%;
}
</style>