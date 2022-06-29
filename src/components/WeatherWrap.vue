<template>
    <div class="weather-wrap">
      <div class="location-box">
        <div class="location">Naihati, India</div>
        <div class="date">Wednesday 29 June, 2022</div>
      </div>

      <div class="weather-box">
        <div class="temp">35&#8451;</div>
        <div class="weather">Rain</div>
      </div>
    </div>
</template>

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
  font-size: 100px;
  font-weight: 900;
  text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
  background-color: rgba(255, 255, 255, 0.25);
  border-radius: 15px;
  margin: 30px 0;
  box-shadow: 3px 6px rgba(0, 0, 0, 0.25);
}
.weather-box .weather{
  color: white;
  font-size: 40px;
  font-weight: 700;
  font-style: italic;
  text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
}
</style>