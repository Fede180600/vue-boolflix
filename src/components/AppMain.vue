<template>
    <section class="contents_list_container py-4">
        <div class="container">
            <h2>film</h2>
            <div class="row row-cols-3 row-cols-md-4 row-cols-lg-6 justify-content-center align-items-center">
                <AppCard v-for="item in resultedFilms" :key="item.id" :film="item"/>
                <!-- <div class="my_card" v-for="item in resultedFilms" :key="item.id">
                    <div class="img_container">
                        <img v-if="item.poster_path" :src="`http://image.tmdb.org/t/p/w342/${item.poster_path}`" alt="">
                        <div v-else style="color: white; font-size: 15px; text-align: center; background-color: rgba(0, 0, 0, .2);">copertina non disponibile</div>
                    </div>
                    <div class="card_text">
                        <h3>titolo film: {{ item.title }}</h3>
                        <p>titolo originale: {{ item.original_title }}</p>
                        <div v-if="countryFlag.includes(item.original_language.toUpperCase())">Lingua originale: <img
                                :src="`https://catamphetamine.gitlab.io/country-flag-icons/3x2/${item.original_language.toUpperCase()}.svg`"
                                alt="" class="language"></div>
                        <p v-else>Lingua originale: {{ item.original_language }}</p>
                        <p v-if="item.vote_average == 0">voto: {{ item.vote_average }}</p>
                        <ul v-else class="stars">
                            Voto:
                            <li v-for="(star, index) in getStars(item.vote_average)" :key="index">
                                <span class="fas fa-star"></span>
                            </li>
                        </ul>
                        <p v-if="item.overview">Overview: <small>{{ item.overview }}</small></p>
                        <p v-else>Missing overview</p>
                    </div>
                </div> -->
            </div>
            <h2 class="mt-2">serie tv</h2>
            <div class="row row-cols-3 row-cols-md-4 row-cols-lg-6 justify-content-center align-items-center">
                <AppCard v-for="item in resultedSeries" :key="item.id" :serie="item"/>
                <!-- <div class="my_card" v-for="item in resultedSeries" :key="item.id">
                    <div class="img_container" style="position: relative;">
                        <img v-if="item.poster_path" :src="`http://image.tmdb.org/t/p/w342/${item.poster_path}`" alt="">
                        <div v-else style="color: white; font-size: 15px; text-align: center; background-color: rgba(0, 0, 0, .2);">copertina non disponibile</div>
                    </div>
                    <div class="card_text">
                        <h3>nome serie TV: {{ item.name }}</h3>
                        <p>nome originale: {{ item.original_name }}</p>
                        <div v-if="countryFlag.includes(item.original_language.toUpperCase())">Lingua originale: <img
                                :src="`https://catamphetamine.gitlab.io/country-flag-icons/3x2/${item.original_language.toUpperCase()}.svg`"
                                alt="" class="language"></div>
                        <p v-else>Lingua originale: {{ item.original_language }}</p>
                        <p v-if="item.vote_average == 0">voto: <i class="fas fa-star"></i></p>
                        <ul v-else class="stars">
                            Voto:
                            <li v-for="(star, index) in getStars(item.vote_average)" :key="index">
                                <span class="fas fa-star"></span>
                            </li>
                        </ul>
                        <p v-if="item.overview">Overview: <small>{{ item.overview }}</small></p>
                        <p v-else>Missing overview</p>
                    </div>
                </div> -->
            </div>
        </div>
    </section>
</template>

<script>
import AppCard from "./AppCard.vue";
export default {
    name: "AppMain",
    components: {
        AppCard
    },
    props: {
        resultedFilms: Array,
        resultedSeries: Array,
    },
    // data() {
    //     return {
    //         countryFlag: []
    //     }
    // },
    // created() {
    //     let countryFlagIcons = require("country-flag-icons");
    //     this.countryFlag = countryFlagIcons.countries;
    // },
    methods: {
        getStars(vote) {
            return Math.ceil(vote / 2);
            // let rating = "";
            // if (voteTransformed >= 0 && voteTransformed <= 1){
            //     rating += `<i class="fas fa-star" style="color: orange"></i>`;
            // } else if(voteTransformed >= 1 && voteTransformed <= 2) {
            //     rating += `<i class="fas fa-star" style="color: orange"</i><i class="fas fa-star" style="color: orange"></i>`;
            // } else if(voteTransformed >= 2 && voteTransformed <= 3) {
            //     rating += `<i class="fas fa-star" style="color: orange"</i><i class="fas fa-star" style="color: orange"></i>`;
            // } else if(voteTransformed >= 3 && voteTransformed <= 4) {
            //     rating += `<i class="fas fa-star" style="color: orange"</i><i class="fas fa-star" style="color: orange"></i>`;
            // } else if(voteTransformed >= 4 && voteTransformed <= 5) {
            //     rating += `<i class="fas fa-star" style="color: orange"</i><i class="fas fa-star" style="color: orange"></i>`;
            // } else if(voteTransformed >= 5) {
            //     rating += `<i class="fas fa-star" style="color: orange"</i><i class="fas fa-star" style="color: orange"></i>`;
            // }
            // return rating;
        }
    },
}
</script>
<style lang="scss" scoped>
@import '~@fortawesome/fontawesome-free/css/all.min.css';

.contents_list_container {
    height: calc(100% - 60px);
    background-color: #1b1b1b;
    overflow-y: auto;

    .container>h2 {
        color: white;
        text-transform: uppercase;
        text-align: center;
    }

    .my_card {
        padding: 0;
        background-color: #1b1b1b;
        margin: 2px;
        min-height: 240px;
        overflow-y: auto;
        .img_container {
            height: 100%;
            overflow: hidden;
        }

        .card_text {
            display: none;
            height: 22vw;
            max-height: 330px;
            min-height: 100%;
            color: white;
            h3 {
                text-transform: uppercase;
                font-size: 14px;
            }
            p, ul, div {
                text-transform: uppercase;
                font-size: 14px;
            }
            .language {
                width: 20px;
                height: 15px;
                object-fit: cover;
            }

            .stars {
                display: flex;
                justify-content: flex-start;
                align-items: center;
                padding-left: 0;

                li {
                    color: orange;
                    margin: 0 2px;
                    font-size: 13px;
                }
            }
        }

    }
    .my_card:hover .img_container {
        display: none;
    }
    .my_card:hover .card_text {
        display: block;
    }
}
</style>