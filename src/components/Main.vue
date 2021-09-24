<template>
  <main> <!-- sfondo generale -->
      <div class="container"> <!-- contenitore delle rispettive 'carte' -->
        <div class="card" v-for="(info, index) in movieList" :key="index">
            <h3>{{info.title}}</h3>
            <h5>{{info.original_title}}</h5>
            <p>{{info.original_language}}</p>
            <p>{{info.vote_average}}</p>
        </div>
      </div>
  </main>
</template>

<script>
export default {
    name: 'Main',
    props: ['movieList'],
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
            width: calc(100% / 5 - 80px);
            background-color: #fff;
            margin: 40px
        }
    }
}



</style>
