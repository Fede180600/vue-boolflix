<template>
    <div class="my_card">
        <div class="img_container">
            <img v-if="item.poster_path" :src="`http://image.tmdb.org/t/p/w342/${item.poster_path}`" alt="">
            <div v-else style="color: white; font-size: 15px; text-align: center; background-color: rgba(0, 0, 0, .2);">
                copertina non disponibile</div>
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
    </div>
</template>
<script>
export default {
    name: "AppCard",
    props: {
        film: Object,
        serie: Object
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
}
</script>
<style lang="scss" scoped>
</style>