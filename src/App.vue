<template>
  <div id="app">
    <Header @ricerca="researchMovie"/>
    <Main :films="filmsArray" :range= "rangeRequired"/>
  </div>
</template>

<script>
import axios from "axios";
import Header from "@/components/Header.vue";
import Main from "@/components/Main.vue";
export default {
  name: 'App',
  components: {
    Header,
    Main
  },
  data() {
    return {
      apiUrl: 'https://api.themoviedb.org/3/search/movie',
      tvUrl: 'https://api.themoviedb.org/3/search/tv',
      apikey: '20f2e48348860ecfa91f99da107394ca',
      language: 'it-IT',
      filmsArray: '',
      range: '',
      rangeRequired:'',
      tvArray: ''
      
      
      
    }
  },
  methods: {
    researchMovie(text) {
      this.range = text;
      const request = {
            params: {
                   api_key: this.apikey,
                   language: this.language,
                   query: text
                 }
      };
      axios
          .all([
              axios.get(this.apiUrl, request),
              axios.get(this.tvUrl, request)
          ])
          .then(axios.spread(respMovie, respTv))
    }
  }
}
</script>