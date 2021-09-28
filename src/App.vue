<template>
  <div id="app">
    <!-- @valore è il nome che passiamo dall'header - getQuery è il metodo per pescare il valore -->
    <Header @valore="getQuery" />
    <!-- ' :movieList ' lo passo al main - movieList lo passo a App -->
    <Main :movieList="movieList" :serieList="serieList"  />
    <!-- <Main /> -->
  </div>
</template>

<script>
import axios from 'axios';
import Header from './components/Header.vue'
import Main from './components/Main.vue'


export default {
  name: 'App',
  components: {
    Header,
    Main
  },
  data() {
        return {
          APIUrl: 'https://api.themoviedb.org/3/search/',
          movie: 'movie',
          serie: 'tv',
          apiKey: '?api_key=6c704469f7f432852b78e2c720d30f40',
          urlQuery: '&query=',
          query:'',
          movieList:[],
          serieList: [],
        }
  },

  methods: {
        getMovieList(){
          axios
                .get(this.APIUrl + this.movie + this.apiKey + this.urlQuery + this.query)
                .then( res => {
                  this.movieList = res.data.results
                    console.log(this.movieList)
                })
        },
         getSerieList(){
          axios
                .get(this.APIUrl + this.serie + this.apiKey + this.urlQuery + this.query)
                .then( res => {
                  this.serieList = res.data.results
                    console.log(this.serieList)
                })
        },

        getQuery(text) {
          this.query = text;
          this.getMovieList()
          this.getSerieList()
        },
  },
}
</script>

<style lang="scss">
@import './style/general.scss';

#app {
  width: 100%;
  height: 100vh;
}

</style>
