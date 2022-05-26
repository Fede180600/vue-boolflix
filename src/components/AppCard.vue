<template>
    <div class="my_card">
        <div class="img_container">
            <img :src="posterUrl" alt="">
        </div>
        <div class="card_text">
            <h3>titolo film: {{ cardObj.title ? cardObj.title : cardObj.name }}</h3>
            <p>titolo originale: {{ cardObj.original_title ? cardObj.original_title : cardObj.original_name }}</p>
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
    computed: {
        posterUrl() {
            return this.cardObj.poster_path
            ? `http://image.tmdb.org/t/p/w342/${this.cardObj.poster_path}`
            : require("../assets/img/no-image.jpg")
        }
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

        h3 {
            text-transform: uppercase;
            font-size: 14px;
        }

        p,
        ul,
        div {
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
</style>