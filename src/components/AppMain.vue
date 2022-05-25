<template>
    <section class="contents_list_container py-4">
        <div class="container">
            <h2>film</h2>
            <div class="row row-cols-3 row-cols-md-4 row-cols-lg-6 justify-content-center align-items-center">
                <AppCard v-for="item in resultedFilms" :key="item.id" :cardObj="item"/>
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
                <AppCard v-for="item in resultedSeries" :key="item.id" :cardObj="item"/>
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
}
</style>