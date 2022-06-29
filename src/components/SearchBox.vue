<template>
    <main>
      <div class="search-box">
        <input type="text" class="search-bar" placeholder="Search...">
      </div>
      <weather-wrap/>
    </main>
</template>

<script>
import WeatherWrap from './WeatherWrap.vue';

export default {
  components:{
    WeatherWrap,
    }
}
</script>

<style scoped>
main{
  min-height: 100vh;
  padding: 25px;

  background-image: linear-gradient(to bottom, rgba(0,0,0,0.25), rgba(0,0,0,0.75));
}
.search-box{
  width: 100%;
  margin-bottom: 30px;
}
.search-box .search-bar{
  display: block;
  width: 50%;
  padding: 15px;
  margin: 0 auto;
  color: #313131;
  font-size: 20px;
  appearance: none;
  outline: none;
  border: none;
  background: none;
  background-color: rgba(255, 255, 255, 0.5);
  box-shadow: 0 0 7px rgba(0, 0, 0,0.25);
  border-radius: 0 15px;
  transition: 0.5s;
}
.search-box .search-bar:focus{
  box-shadow: 0 0 15px rgba(0, 0, 0,0.25);
  background-color: rgba(255, 255, 255, 0.75);
  border-radius: 15px 0;
}
</style>