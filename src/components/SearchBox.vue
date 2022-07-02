<template>
    <main>
      <div class="search-box">
        <input type="text" class="search-bar" placeholder="Search City..." v-model="query" @keypress="fetchResponse">
      </div>
      <weather-wrap :weather-details='weather' v-if="showData && !isError"/>
      <base-title v-else/>
    </main>
</template>

<script>
import WeatherWrap from './WeatherWrap.vue';
import BaseTitle from './BaseTitle.vue';

export default {
  emits:['error-message'],
  props:['apiKey','baseUrl'],
  components:{
    WeatherWrap,
    BaseTitle
    },
    data(){
      return{
        query: '',
        weather: {},
        showData: false,
        isError: false,
      }
    },
    methods:{
     fetchResponse(e){
        if(e.key == "Enter"){
          fetch(`${this.baseUrl}weather?q=${this.query}&units=metric&APPID=${this.apiKey}`)
          .then(res =>{
            if(!res.ok){
               return Promise.reject(res.statusText || 'Something went wrong!');
            }
            return res.json();
          }).then(this.setResults)
          .catch(error => {
           // console.log('error logged:',error);
            this.isError = true;
            this.$emit('error-message',error);
          });
        }
      },
      setResults(results){
        this.weather = results;
        this.showData = true;
        this.isError = false;
        console.log(this.weather)
      }
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