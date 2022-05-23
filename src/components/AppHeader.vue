<template>
    <header>
       <h2>boolflix</h2> 
       <div class="searchbar_container">
           <input placeholder="Cerca film/serie TV" type="text">
           <button class="search_btn">cerca</button>
       </div>
    </header>
</template>

<script>
export default {
    name: "AppHeader",
}
</script>

<style lang="scss" scoped>
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
    }
}
</style>