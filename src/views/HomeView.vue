<template>
  <div id="app" :class="typeof weather.currentConditions != 'undefined' && weather.currentConditions.temp.c > 20 ? 'warm' : ''">

    <main>
      <div class="search-box">
        <input type="text" class="search-bar"  placeholder="Search for city..." v-model="query" @keypress="fetchWeather" />
        <div class="search"></div>
      </div>

      <h1 class="animate__animated animate__fadeInUp" v-if="weather.status == 'fail'"> Oh no</h1>
      <div class="weather-wrap-current" v-if="typeof weather.currentConditions != 'undefined'">
        <div class="local-box">
          <div class="location">{{ weather.region }}</div>
          <div class="date">{{weather.currentConditions.dayhour}}</div>
        </div>

        <div class="weather-box">
          <div class="animate__animated animate__backInUp" id="definition">
            <div class="temp">
              <img class="img0" v-bind:src="weather.currentConditions.iconURL" style="width:150px;height:150px;">
              {{ weather.currentConditions.temp.c }}°c
              <h1 class="pressure">Pressure: {{weather.currentConditions.precip}}, Humid: {{weather.currentConditions.humidity}}</h1>
              <!-- <h1 class="humidity">Humidity: {{weather.currentConditions.humidity}}</h1> -->
            </div>
            <div class="description">{{weather.currentConditions.comment}}</div>
          </div>
      </div>
      <div class = "chart">
          
          
        <div class="animate__animated animate__fadeInUp animate__delay-1s">
            <img class="img1" v-bind:src="weather.next_days[0].iconURL"  style="width:150px;height:150px;margin-left: 0px;">
            <h1 class="day1">{{weather.next_days[0].day}} </h1>
            <h1 class="description1">{{weather.next_days[0].comment}}</h1>
            <h1 class="temp1">{{ weather.next_days[0].min_temp.c }}°c - {{ weather.next_days[0].max_temp.c }}°c</h1>
        </div>
        
        
        <div class="animate__animated animate__fadeInUp animate__delay-2s">
              <img class="img2" v-bind:src="weather.next_days[1].iconURL"  style="width:150px;height:150px;margin-left: 0px;">
              <h1 class="day2">{{weather.next_days[1].day}} </h1>
              <h1 class="description2">{{weather.next_days[1].comment}}</h1>
              <h1 class="temp2">{{ weather.next_days[1].min_temp.c }}°c - {{ weather.next_days[1].max_temp.c }}°c</h1>
        </div>

        <div class="animate__animated animate__fadeInUp animate__delay-1s">
          <img class="img3" v-bind:src="weather.next_days[2].iconURL"  style="width:150px;height:150px;margin-left: 0px;">
              <h1 class="day3">{{weather.next_days[2].day}} </h1>
              <h1 class="description3">{{weather.next_days[2].comment}}</h1>
              <h1 class="temp3">{{ weather.next_days[2].min_temp.c }}°c - {{ weather.next_days[2].max_temp.c }}°c</h1>
        </div>

        <div class="animate__animated animate__fadeInUp animate__delay-2s">
          <img class="img4" v-bind:src="weather.next_days[3].iconURL"  style="width:150px;height:150px;margin-left: 0px;">
              <h1 class="day4">{{weather.next_days[3].day}} </h1>
              <h1 class="description4">{{weather.next_days[3].comment}}</h1>
              <h1 class="temp4">{{ weather.next_days[3].min_temp.c }}°c - {{ weather.next_days[3].max_temp.c }}°c</h1>
        </div>

        <div class="animate__animated animate__fadeInUp animate__delay-1s">
          <img class="img5" v-bind:src="weather.next_days[4].iconURL"  style="width:150px;height:150px;margin-left: 0px;">
              <h1 class="day5">{{weather.next_days[4].day}} </h1>
              <h1 class="description5">{{weather.next_days[4].comment}}</h1>
              <h1 class="temp5">{{ weather.next_days[4].min_temp.c }}°c - {{ weather.next_days[4].max_temp.c }}°c</h1>
        </div>

        <div class="animate__animated animate__fadeInUp animate__delay-2s">
          <img class="img6" v-bind:src="weather.next_days[5].iconURL"  style="width:150px;height:150px;margin-left: 0px;">
              <h1 class="day6">{{weather.next_days[5].day}} </h1>
              <h1 class="description6">{{weather.next_days[5].comment}}</h1>
              <h1 class="temp6">{{ weather.next_days[5].min_temp.c }}°c - {{ weather.next_days[5].max_temp.c }}°c</h1>
        </div>

        <div class="animate__animated animate__fadeInUp animate__delay-1s">
          <img class="img7" v-bind:src="weather.next_days[6].iconURL"  style="width:150px;height:150px;margin-left: 0px;">
              <h1 class="day7">{{weather.next_days[6].day}} </h1>
              <h1 class="description7">{{weather.next_days[6].comment}}</h1>
              <h1 class="temp7">{{ weather.next_days[6].min_temp.c }}°c - {{ weather.next_days[6].max_temp.c }}°c</h1>
        </div>
      </div>
      </div>
    </main>
  </div>
</template>

<script>

export default {
    name: "app",

    data() {
        return {
            url_base: "https://weatherdbi.herokuapp.com/data/weather/",
            query: "",
            weather: {}
        };
    },
    methods: {
        fetchWeather(e) {
            if (e.key == "Enter") {
                fetch(`${this.url_base}${this.query}`)
                    .then(res => {
                    return res.json();
                }).then(this.setResults);
            }
        },
        setResults(results) {
            this.weather = results;
        },
    },
}
</script>
<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'montserrat', sans-serif;
 }

#app {
  background-size: cover;
  background-position: bottom;
  transition: 0.4s;
}

main {
  min-height: 100vh;
  padding: 25px;
  background-image: linear-gradient(to bottom, rgba(102, 126, 234, 1), rgba(118, 75, 162, 1));
}

.search-box {
  width: 50%;
  margin-bottom: 30px;
}

.search-box .search-bar {
  display: block;
  width: 50%;
  padding: 15px;

  color: #313131;
  font-size: 20px;
  appearance: none;
  border: none;
  outline: none;
  background: none;
  box-shadow: 0px 0px 8px rgba(0, 0, 0, 0.25);
  background-color: rgba(255, 255, 255, 0.5);
  border-radius: 0px 16px 0px 16px;
  transition: 0.4s;
}

.search-box .search-bar:focus {
  box-shadow: 0px 0px 16px rgba(0, 0, 0, 0.25);
  background-color: rgba(255, 255, 255, 0.75);
  border-radius: 16px 0px 16px 0px;
}

.local-box .location {
  float: left;
  color: #FFF;
  font-size: 32px;
  font-weight: 500;
  text-align: center;
  text-shadow: 1px 3px rgba(0, 0, 0, 0.25);
  width:100% ;
}

.local-box .date {
  width: 100%;
  float: right;
  color: #FFF;
  font-size: 20px;
  font-weight: 300;
  font-style: italic;
  text-align: center;
}

.weather-box {
  text-align: left;
}

#definition {
  display: block;
  box-sizing: content-box;
  flex-direction: column;
  justify-content: center;
  align-items: left;
  margin-bottom: 30px;
}
.pressure{
  font-size: 15px !important;
  font-weight: 300;
  font-style: italic;
  text-align: center;
  text-shadow: none  !important;;
}
.temp {
  display: inline-block;
  padding: 10px 25px;
  color: #FFF;
  font-size: 102px;
  font-weight: 900;
  text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
  background-color: rgba(255, 255, 255, 0.25);
  border-radius: 16px;
  margin: 50px 0px;
  margin-left: 37%;
  box-shadow: 3px 6px rgba(0, 0, 0, 0.25);
  text-align: center;
}
.img0{
  float: left;
}

.weather-box .weather {
  color: #FFF;
  font-size: 48px;
  font-weight: 700;
  font-style: italic;
  text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
}
h1{
  color: #FFF !important;
  font-size: 20px !important;
  text-align: center !important;
}

.description{
  color: #FFF;
  font-size: 50px;
  font-weight: 900;
  text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
  text-align: center;
  margin: 10px 0px;
}
.chart{
  display: flex;
  justify-content: center;
  align-items: center;
  width:100%;
  margin-top: 20px;
}
.chart>div{
  display: block;
  width:230px;
  height:460px;
  border: 1px solid rgb(0, 0, 0);
  background-color: rgba(255, 255, 255, 0.05);
  box-shadow: 3px 6px rgba(0, 0, 0, 0.15);
  border-radius: 10px;
  margin: 0px 10px;
}

</style>