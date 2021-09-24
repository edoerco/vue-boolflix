<template>
  <div>
    <!-- @valore è il nome che passiamo dall'header - getQuery è il metodo per pescare il valore -->
    <Header @valore="getQuery" />
    <!-- ' :movieList ' lo passo al main - movieList lo passo a App -->
    <Main :movieList="movieList" />
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
          APIUrl: 'https://api.themoviedb.org/3/search/movie?api_key=6c704469f7f432852b78e2c720d30f40&query=', // trasformare la query
          movieList:[],
          query:'',
        }
    },

    created() {
        this.getMovieList()
    },

    methods: {
        getMovieList(){
          axios
                .get(this.APIUrl + this.query)
                .then( res => {
                  this.movieList = res.data.results
                    console.log(this.movieList)
                })
        },

        getQuery(text) {
          this.query = text;
          this.getMovieList()
        },
    },
}
</script>

<style lang="scss">
@import './style/general.scss';

</style>
