<template>
    <header>
        <div class="logo_container">
            <img src="../assets/img/logo.png" alt="">
        </div>
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

    .logo_container {
        width: 150px;
        img {
            height: 100%;
        }
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