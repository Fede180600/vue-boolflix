<template>
    <div class="my_card">
        <div class="img_container">
            <img :src="imageUrl" alt="">
        </div>
        <div class="card_text">
            <h3>{{ getCardTitle }}</h3>
            <p v-if="cardObj.title">Titolo Originale: {{ getCardSecondTitle }}</p>
            <p v-else>Nome Originale: {{ getCardSecondTitle }}</p>
            <div v-if="countryFlag.includes(cardObj.original_language.toUpperCase())">Lingua originale: <img
                    :src="`https://catamphetamine.gitlab.io/country-flag-icons/3x2/${cardObj.original_language.toUpperCase()}.svg`"
                    alt="" class="language"></div>
            <p v-else>Lingua originale: {{ cardObj.original_language }}</p>
            <p v-if="cardObj.vote_average == 0">voto: {{ cardObj.vote_average }}</p>
            <ul v-else class="stars">
                Voto:
                <li v-for="(star, index) in getStars(cardObj.vote_average)" :key="index">
                    <span class="fas fa-star"></span>
                </li>
            </ul>
            <p v-if="cardObj.overview">Overview: <small>{{ cardObj.overview }}</small></p>
            <p v-else>Missing overview</p>
        </div>
    </div>
</template>
<script>
export default {
    name: "AppCard",
    props: {
        cardObj: Object
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
            return Math.ceil(vote / 2);
        }
    },
    computed: {
        imageUrl() {
            return this.cardObj.poster_path
            ? `http://image.tmdb.org/t/p/w342/${this.cardObj.poster_path}`
            : require("../assets/img/no-image.jpg")
        },
        getCardTitle() {
            return this.cardObj.title ? this.cardObj.title : this.cardObj.name;
        },
        getCardSecondTitle() {
            return this.cardObj.original_title ? this.cardObj.original_title : this.cardObj.original_name;
        },
    },
}
</script>
<style lang="scss" scoped>
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
        text-transform: uppercase;
        font-size: 14px;

        h3 {
            text-transform: uppercase;
            font-size: 18px;
            font-weight: 600;
            text-align: center;
            margin: 5px 0;
            color: #db202c;
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
</style>