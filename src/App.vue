<template>
  <div id="app">
    <div class="app-wrap">
      <!-- header -->
      <AppHeader @userSearch="search($event)" />
      <!-- films list -->
      <AppMain :resultedFilms="this.films" :resultedSeries="this.series"/>
    </div>
  </div>
</template>

<script>
import AppHeader from "./components/AppHeader.vue";
import AppMain from "./components/AppMain.vue";
import axios from "axios";

export default {
  name: 'App',
  components: {
    AppHeader,
    AppMain,
  },
  data: function () {
    return {
      films: [],
      series: [],
      apiKey: "7c8de487b8a14f4c4fd050c515a00d5e",
    };
  },
  methods: {
    search(searchThisString) {
      const options = {
        params: {
          api_key: this.apiKey,
          query: searchThisString 
        }
      };

      const filmsReq = axios.get('https://api.themoviedb.org/3/search/movie', options);
      const seriesReq = axios.get('https://api.themoviedb.org/3/search/tv', options);

      axios.all([filmsReq, seriesReq]).then(resp => {
        this.films = resp[0].data.results;
        this.series = resp[1].data.results;
      });
    },
  },
};
</script>

<style lang="scss">
@import "./style/common.scss";
</style>
