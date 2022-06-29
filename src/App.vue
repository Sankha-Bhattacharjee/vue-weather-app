<template>
  <div id="app">
    <search-box/>
  </div>
</template>

<script>
import SearchBox from './components/SearchBox.vue';
export default {
  name: 'App',
  components:{
    SearchBox,
  },
  data(){
    return {
      api_key:'2b187d8543d96d8cee3cc12e77f94d6b',
    };
  }
}
</script>

<style>
*{
  margin:0;
  padding: 0;
  box-sizing: border-box;
}

body{
  font-family: 'montserrat', sans-serif;
}

#app{
  background-image: url('./assets/bg.jpg');
  background-size: cover;
  background-position: bottom;
  transition: 0.5s;
}
</style>
