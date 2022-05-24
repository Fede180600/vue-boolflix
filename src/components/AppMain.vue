<template>
    <section class="films_list_container py-4">
        <div class="container">
            <div class="row row-cols-2 row-cols-md-5 justify-content-center align-items-center">
                <div class="film_card" v-for="film in resultedFilms" :key="film.id">
                    <h3>titolo film: {{ film.title }}</h3>
                    <p>titolo originale: {{ film.original_title}}</p>
                    <div v-if="film.original_language">Lingua originale: <img :src="`https://catamphetamine.gitlab.io/country-flag-icons/3x2/${film.original_language.toUpperCase()}.svg`" alt="" class="film_language"></div>
                    <p v-else>Lingua originale: {{ film.original_language }}</p>
                    <p>voto: {{ film.vote_average }}</p>
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
    }
}
</script>

<style lang="scss" scoped>
.films_list_container {
    height: calc(100% - 60px);
    background-color: #434343;
    overflow-y: auto;
    .film_card {
    max-height: 400px;
    min-height: 400px;
    padding: 20px 10px;
    border: 1px solid white;
    margin: 10px 10px;
    .film_language {
        width: 15px;
        height: 10px;
        object-fit: cover;
    }
}
}
</style>