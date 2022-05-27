<template>
    <section class="contents_list_container py-4">
        <div class="container">
            <h2>film</h2>
            <div class="row row-cols-3 row-cols-md-4 row-cols-lg-6 justify-content-center align-items-center">
                <AppCard v-for="item in resultedFilms" :key="item.id" :cardObj="item"/>
            </div>
            <h2 class="mt-2">serie tv</h2>
            <div class="row row-cols-3 row-cols-md-4 row-cols-lg-6 justify-content-center align-items-center">
                <AppCard v-for="item in resultedSeries" :key="item.id" :cardObj="item"/>
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