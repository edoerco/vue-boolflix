<template>
  <main> <!-- sfondo generale -->
      <div class="container"> <!-- contenitore delle rispettive 'carte' -->

      <!-- movie -->
        <div class="card" v-for="(info, index) in movieList" :key="index">
            <div class="images">
                <img v-if="info.poster_path != null" :src="'http://image.tmdb.org/t/p/w342' + info.poster_path" alt="">
                <img  v-else src="../assets/image-not-found.png" alt="">
            </div>
            <div class="card-text">
                <h2>Titolo: {{info.title}}</h2>
                <h5>Titolo originale: {{info.original_title}}</h5>
                <p>Overview: {{info.overview}}</p>
                <country-flag :country='getFlag(info.original_language)' size='mediums'/>
                <!-- <p>{{info.original_language}}</p> trasformare la lingua in una bandiera -->
                <div class="star">
                    Voto: <fa icon="star" v-for="(star, index) in 5" :key="index" :class="colorStar(info.vote_average, star)"/>
                </div>
            </div>
        </div>

        <!-- serie -->
        <div class="card" v-for="(info, index) in serieList" :key="index">
            <div class="images">
                <img v-if="info.poster_path != null" :src="'http://image.tmdb.org/t/p/w342' + info.poster_path" alt="">
                <img  v-else src="../assets/image-not-found.png" alt="">
            </div>
            <div class="card-text">
                <h2>Titolo: {{info.name}}</h2>
                <h5>Titolo originale: {{info.original_name}}</h5> 
                <p>Overview: {{info.overview}}</p>
                <country-flag :country='getFlag(info.original_language)' size='mediums'/>
                <!-- <p>{{info.original_language}}</p> trasformare la lingua in una bandiera -->
                <div class="star">
                    Voto: <fa icon="star" v-for="(star, index) in 5" :key="index" :class="colorStar(info.vote_average, star)"/>
                </div>
            </div>
        </div>
      </div>
  </main>
</template>

<script>
import CountryFlag from 'vue-country-flag'

export default {
    name: 'Main',
    props: ['movieList','serieList'],
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
            Math.ceil(this.info.vote_average / 2)
        },

        colorStar(vote, star) {
            vote = Math.ceil(vote / 2)
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
    height: calc(100vh - 100px); // altezza momentanea, rimuoverla a fine lavoro
    background-color: $main-color;
    overflow-y: auto;

    .container{
        display: flex;
        flex-wrap: wrap;
        height: 100%;
        width: 90%;
        margin: 0 auto;
        background-color: transparent;
        perspective: 1000px;

        .card {
            position: relative;
            display: flex;
            flex-direction: column;
            align-items: center;
            width: calc(100% / 5 - 20px);
            height: 600px;
            color: #fff;
            margin: 20px 10px;
            padding: 0 10px;
            transition: transform 0.6s;
            transform-style: preserve-3d;

            &:hover {
                transform: rotateY(180deg);
            }

            .images {
                position: absolute;
                height: 100%;
                width: 100%;
                backface-visibility: hidden;
            }

            img {
                width: 100%;
                height: 100%;
                object-fit: fill;
            }

            .card-text {
                position: absolute;
                text-align: center;
                display: flex;
                flex-direction: column;
                align-items: center;
                justify-content: center;
                background-color: $primary;
                color: white;
                transform: rotateY(180deg);
                height: 100%;
                width: 100%;
                backface-visibility: hidden;
                padding: 0 10px;
            }

            p,
            country-flag,
            .star {
                margin: 10px 0;
            }

        }
    }
}

.gold {
    color: rgb(233, 212, 30);
}

</style>
