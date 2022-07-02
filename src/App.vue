<template>
  <div id="app">
    <search-box :api-key='api_key' :base-url='url_base' @error-message="getErrorMessage"/>
    <base-dialog :error-Text="errorText" :show="showErrorDialogue" @close="closeDialog"/>
  </div>
</template>

<script>
import SearchBox from './components/SearchBox.vue';
import BaseDialog from './components/BaseDialog.vue';
export default {
  name: 'App',
  components:{
    SearchBox,
    BaseDialog
  },
  data(){
    return {
      api_key:'2b187d8543d96d8cee3cc12e77f94d6b',
      url_base: 'https://api.openweathermap.org/data/2.5/',
      errorText:'',
      showDialogue: false
    };
  },
  computed:{
    showErrorDialogue(){
      return this.showDialogue;
    }
  },
  methods:{
    getErrorMessage(msg){
     // console.log('error msg in APP',msg);
      this.errorText = msg;
      this.showDialogue = true;
    },
    closeDialog(){
      this.showDialogue = false;
    }
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
