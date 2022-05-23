<template>
  <div id="app">
    <div class="app-wrap">
      <!-- header -->
      <AppHeader />
      <!-- films list -->
      <AppFilmsList />
    </div>
  </div>
</template>

<script>
import AppHeader from "./components/AppHeader.vue";
import AppFilmsList from "./components/AppFilmsList.vue";

export default {
  name: 'App',
  components: {
    AppHeader,
    AppFilmsList,
  }
}
</script>

<style lang="scss">
@import "./style/common.scss";
</style>
