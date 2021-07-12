<template>
  <div id="app">
    
    <Header msg="Boolflix" @apiMod="newApi" /> 

    <Main v-for="(film,index) in filmList" :key="index"
      :title="film.title"
      :originalTitle="film.original_title"
      :language="film.original_language"
      :vote="film.vote_average"/>   
    
  </div>
</template>

<script>
import axios from 'axios';
import Header from './components/Header.vue'
import Main from './components/Main.vue'
export default {
  name: 'App',
  data(){
    return {
      apiURL: '',
      filmList: []
    }
  },
  components: {
    Header,
    Main
  },
  methods: {
    newApi(apiModify){
      this.apiURL = apiModify;
      console.log(this.apiURL);
      this.getFilm();
    },
  
    getFilm(){
      axios
        .get(this.apiURL)
        .then(response => {
          this.filmList = response.data.results;
          console.log(this.filmList);
        })
        .catch(error => {
          console.log("Errore : " + error);
        })
    }
  },
}
</script>