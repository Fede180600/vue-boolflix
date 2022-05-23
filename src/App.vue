<template>
  <div id="app">
    <div class="app-wrap">
      <!-- header -->
      <AppHeader @searchFilmTitle="filmSearched($event)" />
      <!-- films list -->
      <AppFilmsList :resultedFilms="this.films" />
    </div>
  </div>
</template>

<script>
import AppHeader from "./components/AppHeader.vue";
import AppFilmsList from "./components/AppFilmsList.vue";
import axios from "axios";

export default {
  name: 'App',
  components: {
    AppHeader,
    AppFilmsList,
  },
  data: function () {
    return {
      films: [],
      stringToSearch: "",
    };
  },
  methods: {
    filmSearched(title) {
      this.films = [];
      this.stringToSearch = title.toLowerCase();
      axios
      .get('https://api.themoviedb.org/3/search/movie', {
        params: {
          api_key: "7c8de487b8a14f4c4fd050c515a00d5e",
          query: this.stringToSearch,
        }
      })
      .then((resp) => {
        resp.data.results.forEach(film => {
          this.films.push(film);
        });
      })
    }

  }
}
</script>

<style lang="scss">
@import "./style/common.scss";
</style>
