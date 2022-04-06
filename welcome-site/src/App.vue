<template>
 <div class="main">
   <div class="left">
     <div class="clock">
       {{time}}
     </div>
     <div class="search">
       DuckDuckGo <br>
       <input type="text" placeholder="search..." class="duck" @keydown.exact="searchWeb" @keydown.alt="searchAlt" v-model="phrase">
     </div>
     <div class="stocks">
       <StockTable/>
     </div>
     <div class="myApp">
       <WeatherApp class="style"/>
     </div>
   </div>
   <div class="right">
     <WebsiteLinks />
   </div>
  </div>
</template>

<script>
import WeatherApp from './components/WeatherApp.vue'
import WebsiteLinks from './components/WebsiteLinks.vue'
import StockTable from './components/StockTable.vue'

export default {
  name: 'App',
  components: {
    StockTable,
    WeatherApp,
    WebsiteLinks
  },
  data() {
    return {
      myDate: null,
      time: null,
      hour: null,
      minute: null,
      second: null,
      interval: 0,
      url: '',
      phrase: ''
    }
  },
  methods: {
    getTime() {
      this.myDate =  new Date()
      this.hour = this.myDate.getHours()
      if (this.hour<10) {this.hour='0'+ this.hour}
      this.minute = this.myDate.getMinutes()
      if (this.minute<10) {this.minute='0'+ this.minute}
      this.second = this.myDate.getSeconds()
      if (this.second<10) {this.second='0'+ this.second}
      this.time = this.hour + ':' + this.minute + ':' + this.second
    },
    searchWeb(e) {
      if (e.keyCode === 13) {
        console.log('enter zostalo nacisnięte')
        this.url = 'https://duckduckgo.com/?q='+ this.phrase +'&t=ffab&ia=web'
        window.open(this.url)
        this.phrase = ''
      }
    },
    searchAlt(e) {
      if (e.keyCode === 13) {
        console.log('alt + enter zostalo nacisnięte')
        this.url = 'https://duckduckgo.com/?q='+ this.phrase +'&t=ffab&ia=web'
        console.log(this.url)
        window.open(this.url,)
        this.phrase = ''
        focus(this.url)
      }
    }

  },
  mounted() {
    this.getTime()
    this.interval = setInterval(this.getTime, 1000)
  },
  beforeUnmount() {
    clearInterval(this.interval)
  }
  
}
</script>

<style>
#app {
  height: 100vh;
  width: 100vw;
}
body, html {
    margin: 0;
    padding: 0;
    background-color: black;
}
table {
  font-size: 26px;
  height: 100%;
  width: 100%
}
.main {
    color: white;
    display: flex;
    position: relative;
    top: 50%;
    transform: translateY(-50%);
    height: 95%;
    width: 95%;
    margin: auto;
    margin-top: auto;
    justify-content: space-between;
}
.left {
    border: gray solid 2px;
    width: 40%;
}
.right {
  justify-content: center;
  border: gray solid 2px;
  border-left: none;
  width: 60%;
}
.clock {
  height: 15%;
  border-bottom: 2px solid gray;
  font-size: 6vw;
}
.search {
  font-size: 1.75vw;
  height: 10%;
  border-bottom: 2px solid gray;
}
.stocks {
  height: 40%;
}
.duck {
  height: 35%;
  width: 80%;
}
.stocks tr {
 width: 100%;
 height: 20%;
 
}
.style {
  width: 100%;
  height: 100%;
}
.myApp {
  height: 34.5%;
}
.sep {
  border-left: 2px solid gray;
}
.stocks th {
  border-bottom: gray 2px solid;
}













#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}
</style>
