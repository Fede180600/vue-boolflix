<template>
    <section class="contents_list_container py-4">
        <div class="container">
            <h2>film</h2>
            <div class="row row-cols-2 row-cols-md-5 justify-content-center align-items-center">
                <div class="card" v-for="item in resultedFilms" :key="item.id">
                    <div class="img-container">
                        <img v-if="item.poster_path" :src="`http://image.tmdb.org/t/p/w500/${item.poster_path}`"
                            alt="">
                        <p v-else>immagine copertina non disponibile</p>
                    </div>
                    <h3>titolo film: {{ item.title }}</h3>
                    <p>titolo originale: {{ item.original_title }}</p>
                    <div v-if="countryFlag.includes(item.original_language.toUpperCase())">Lingua originale: <img
                            :src="`https://catamphetamine.gitlab.io/country-flag-icons/3x2/${item.original_language.toUpperCase()}.svg`"
                            alt="" class="language"></div>
                    <p v-else>Lingua originale: {{ item.original_language }}</p>
                    <p>voto: {{ getStars(item.vote_average) }}</p>
                </div>
            </div>
            <h2 class="mt-2">serie tv</h2>
            <div class="row row-cols-2 row-cols-md-5 justify-content-center align-items-center">
                <div class="card" v-for="item in resultedSeries" :key="item.id">
                    <div class="img-container">
                        <img v-if="item.poster_path" :src="`http://image.tmdb.org/t/p/w500/${item.poster_path}`"
                            alt="">
                        <p v-else>immagine copertina non disponibile</p>
                    </div>
                    <h3>nome serie TV: {{ item.name }}</h3>
                    <p>nome originale: {{ item.original_name }}</p>
                    <div v-if="countryFlag.includes(item.original_language.toUpperCase())">Lingua originale: <img
                            :src="`https://catamphetamine.gitlab.io/country-flag-icons/3x2/${item.original_language.toUpperCase()}.svg`"
                            alt="" class="language"></div>
                    <p v-else>Lingua originale: {{ item.original_language }}</p>
                    <p>voto: {{ item.vote_average }}</p>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
export default {
    name: "AppMain",
    props: {
        resultedFilms: Array,
        resultedSeries: Array,
    },
    data() {
        return {
            countryFlag: []
        }
    },
    created() {
        let countryFlagIcons = require("country-flag-icons");
        this.countryFlag = countryFlagIcons.countries;
    },
    methods: {
        getStars(vote) {
            const voteTransformed = vote / 2;
            let rating = "";
            if (voteTransformed >= 0 && voteTransformed <= 1){
                rating = `<i class="fas fa-star" style="color: orange"></i>`;
            } else if(voteTransformed >= 1 && voteTransformed <= 2) {
                rating = `<i class="fas fa-star" style="color: orange"</i><i class="fas fa-star" style="color: orange"></i>`;
            } else if(voteTransformed >= 2 && voteTransformed <= 3) {
                rating = `<i class="fas fa-star" style="color: orange"</i><i class="fas fa-star" style="color: orange"></i>`;
            } else if(voteTransformed >= 3 && voteTransformed <= 4) {
                rating = `<i class="fas fa-star" style="color: orange"</i><i class="fas fa-star" style="color: orange"></i>`;
            } else if(voteTransformed >= 4 && voteTransformed <= 5) {
                rating = `<i class="fas fa-star" style="color: orange"</i><i class="fas fa-star" style="color: orange"></i>`;
            } else if(voteTransformed >= 5) {
                rating = `<i class="fas fa-star" style="color: orange"</i><i class="fas fa-star" style="color: orange"></i>`;
            }
            return rating;
        }
    },
}
</script>
<style lang="scss" scoped>
@import '~@fortawesome/fontawesome-free/css/all.min.css';
.contents_list_container {
    height: calc(100% - 60px);
    background-color: #434343;
    overflow-y: auto;

    .container>h2 {
        color: white;
        text-transform: uppercase;
        text-align: center;
    }

    .card {
        max-height: 400px;
        min-height: 400px;
        overflow-y: auto;
        background-color: rgb(165, 165, 165);
        padding: 20px 10px;
        border: 1px solid #b20000;
        margin: 10px 10px;

        .language {
            width: 15px;
            height: 10px;
            object-fit: cover;
        }
    }
}
</style>