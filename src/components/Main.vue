<template>
  <main> <!-- sfondo generale -->
      <div class="container"> <!-- contenitore delle rispettive 'carte' -->
        <!-- <div class="card" v-for="(info, index) in movieList" :key="index">
            <h3>{{info.title}}</h3>
            <h5>{{info.original_title}}</h5>
            <p>{{info.original_language}}</p>
            <p>{{info.vote_average}}</p>
        </div> -->
      </div>
  </main>
</template>

<script>
import axios from 'axios';

export default {
    name: 'Main',
    data() {
        return {
            APIUrl: 'https://api.themoviedb.org/3/search/movie?api_key=6c704469f7f432852b78e2c720d30f40&query=rick',
            movieList:[],
        }
    },

    created() {
        this.getMoviueList()
    },

    methods: {
        getMoviueList(){
            axios
                .get(this.APIUrl)
                .then( res => {
                    this.movieList = res.data.results
                    console.log(this.movieList)
                })
        }
    },
}



</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import '../style/vars.scss';

main {
    width: 100%;
    min-height: 600px; // altezza momentanea, rimuoverla a fine lavoro
    background-color: $main-color;

    .container{
        display: flex;
        flex-wrap: wrap;
        height: 100%;
        width: 90%;
        margin: 0 auto;

        .card {
            height: 300px;
            width: 200px;
            background-color: #fff;
            margin: 10px
        }
    }
}



</style>
