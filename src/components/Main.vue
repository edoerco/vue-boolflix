<template>
  <main> <!-- sfondo generale -->
      <div class="container"> <!-- contenitore delle rispettive 'carte' -->
        <div class="card"> <!-- card che cicleremo per farle ripetere a video -->
        </div>
      </div>
  </main>
</template>

<script>
export default {
  name: 'Main',
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import '../style/vars.scss';

main {
    width: 100%;
    height: 800px; // altezza momentanea, rimuoverla a fine lavoro
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
