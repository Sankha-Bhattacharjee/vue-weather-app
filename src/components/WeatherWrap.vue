<template>
    <div class="weather-wrap">
      <div class="location-box">
        <div class="location">{{location}}</div>
        <div class="date">{{currentDate}}</div>
      </div>

      <div class="weather-box">
        <div class="temp">
          <div class="original-temp">{{temperature}}&#8451;</div>
          <div class="feels-temp">Feels like {{weatherDetails.main.feels_like}}&#8451;</div>
        </div>
        <div class="weather">{{weatherType}}</div>
      </div>
      <div class="other-details-box">
        <div class="humidity">
          Humidity: {{weatherDetails.main.humidity}}%
        </div>
        <div class="pressure">
          Pressure: {{weatherDetails.main.pressure}} hPa
        </div>
        <div class="wind-speed">
          Wind Speed: {{weatherDetails.wind.speed}} m/s
        </div>
      </div>
    </div>
</template>


<script>
export default {
  props: ['weatherDetails'],
  computed:{
    location(){
      return `${this.weatherDetails.name}, ${this.weatherDetails.sys.country}`;
    },
    currentDate(){
      return this.dateFormatter();
    },
    temperature(){
      return Math.round(this.weatherDetails.main.temp);
    },
    weatherType(){
      return this.weatherDetails.weather[0].main;
    }
  },
  methods:{
    dateFormatter(){
      let months = ['January','February','March','April','May','June','July','August','September',
      'October','November','December'];
      let days = ['Sunday','Monday','Tuesday','Wednesday','Thursday','Friday','Saturday']
      let d = new Date();

      let currentDay = days[d.getDay()];
      let currentDate = d.getDate();
      let currentMonth = months[d.getMonth()];
      let currentYear = d.getFullYear();

      return `${currentDay} ${currentDate} ${currentMonth}, ${currentYear}`;
    }
  }
}
</script>

<style scoped>

.location-box .location{
  color: white;
  font-size: 30px;
  font-weight: 500;
  text-align: center;
  text-shadow: 1px 3px rgba(0, 0, 0, 0.25);
}
.location-box .date{
  color: white;
  font-size: 20px;
  font-weight: 300;
  font-style: italic;
  text-align: center;
  text-shadow: 1px 3px rgba(0, 0, 0, 0.25);
}
.weather-box{
  text-align: center;
}
.weather-box .temp{
  display: inline-block;
  padding: 10px 25px;
  color: white;
  background-color: rgba(255, 255, 255, 0.25);
  border-radius: 15px;
  margin: 30px 0;
  box-shadow: 3px 6px rgba(0, 0, 0, 0.25);
}
.weather-box .temp .original-temp{
  font-size: 100px;
  font-weight: 900;
  text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
}
.weather-box .temp .feels-temp{
  font-size: 20px;
  font-style: italic;
}
.weather-box .weather{
  color: white;
  font-size: 40px;
  font-weight: 700;
  font-style: italic;
  text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
}
.other-details-box{
  display: block;
  text-align: center;
  margin: 30px auto;
  width: 300px;
  padding: 10px 15px;
  border-radius: 12px;
  background-color: rgba(255, 255, 255, 0.25);
  box-shadow: 3px 6px rgba(0, 0, 0, 0.25);
}
.humidity,.pressure,.wind-speed{
  color: white;
  font-size: 20px;
  font-weight: 300;
  text-shadow: 3px 3px rgba(0, 0, 0, 0.25);
}
@media only screen and (max-width: 720px){
  .location-box .location{
    font-size: 25px;
  }
  .location-box .date{
    font-size: 17px;
  }
  .weather-box .temp .original-temp{
    font-size: 75px;
    font-weight: 700;
  }
  .weather-box .temp .feels-temp{
    font-size: 17px;
    font-weight: 700;
  }
  .weather-box .weather{
    font-size: 35px;
  }
  .other-details-box{
    margin: 25px auto 0 auto;
    width: 220px;
    padding: 7px 12px;
  }
  .humidity,.pressure,.wind-speed{
    font-size: 17px;
    font-weight: 200;
  }
}
</style>