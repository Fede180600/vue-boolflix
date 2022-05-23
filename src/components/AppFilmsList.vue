<template>
    <section class="films_list_container py-4">
        <div class="container">
            <div class="row row-cols-3 row-cols-md-6 justify-content-center align-items-center">
                <AppFilmCard />
                <AppFilmCard />
                <AppFilmCard />
                <AppFilmCard />
                <AppFilmCard />

            </div>
        </div>
    </section>
</template>

<script>
import AppFilmCard from "./AppFilmCard";
export default {
    name: "AppFilmsList",
    components: {
        AppFilmCard,
    }
}
</script>

<style lang="scss" scoped>
.films_list_container {
    height: calc(100% - 60px);
    background-color: #434343;
    overflow-y: auto;
}
</style>