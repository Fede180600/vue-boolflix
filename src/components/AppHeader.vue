<template>
    <header>
        <h2>boolflix</h2>
        <div class="searchbar_container">
            <input placeholder="Cerca film/serie TV" type="text" v-model="searchedFilm"
                @keyup.enter="$emit('searchFilmTitle', searchedFilm)">
            <button class="search_btn" @click="$emit('searchFilmTitle', searchedFilm)"><i
                    class="fas fa-search"></i></button>
        </div>
    </header>
</template>

<script>

export default {
    name: "AppHeader",
    data: function () {
        return {
            searchedFilm: "",
        };
    },
}
</script>

<style lang="scss" scoped>
@import '~@fortawesome/fontawesome-free/css/all.min.css';

header {
    background-color: #000000;
    height: 60px;
    padding: 0 15px;
    display: flex;
    justify-content: space-between;
    align-items: flex-end;

    h2 {
        text-transform: uppercase;
        color: #b20000;
    }

    .searchbar_container {
        margin-bottom: 10px;
        background-color: #403f47cb;
        input {
            outline: none;
        }
        input,
        button {
            background-color: #403f47cb;
            border: none;
            color: #868686;
            font-weight: 600;
        }
    }
}
</style>