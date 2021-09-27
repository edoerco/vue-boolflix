<template>
  <main> <!-- sfondo generale -->
      <div class="container"> <!-- contenitore delle rispettive 'carte' -->
        <div class="card" v-for="(info, index) in movieList" :key="index">
            <div class="images">
                <img v-if="info.poster_path != null" :src="'http://image.tmdb.org/t/p/w500' + info.poster_path" alt="">
                <img  v-else src="../assets/image-not-found.png" alt="">
            </div>
            <h3>{{info.title}}</h3>
            <h3>{{info.name}}</h3>
            <h5>{{info.original_title}}</h5>
            <h5>{{info.original_name}}</h5>
            <country-flag :country='getFlag(info.original_language)' size='mediums'/>
            <!-- <p>{{info.original_language}}</p> trasformare la lingua in una bandiera -->
            <div class="star">
                <fa icon="star" v-for="(star, index) in 5" :key="index" :class="colorStar(info.vote_average, star)"/>
            </div>
        </div>
      </div>
  </main>
</template>

<script>
import CountryFlag from 'vue-country-flag'

export default {
    name: 'Main',
    props: ['movieList'],
    components: {
        CountryFlag
    },

    data() {
        return {
            valTmp:'',
        }
    },

    created() {
    },

    methods: {
        getFlag(lenguage) {
            if(lenguage == 'en') {
                return 'gb';
            } 
            else if (lenguage == 'ja') {
                return 'jp'
            } 
            return lenguage;
        }, 

        getStars() {
            Math.ceil(parseInt(this.info.vote_average / 2))
        },

        colorStar(vote, star) {
            vote = Math.ceil(parseInt(vote / 2))
            if(star <= vote) {
                return 'gold'
            }
            return null
        },
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
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: space-around;
            text-align: center;
            width: calc(100% / 5 - 80px);
            color: #fff;
            margin: 40px;

            .images {
                height: 80%;
            }

            h3 {
                margin-top: 10px;
            }

            img {
                width: 100%;
            }
        }
    }
}

.gold {
    color: rgb(233, 212, 30);
}

</style>
