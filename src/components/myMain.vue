<template>
    <main>
        <div class="card-container">
            <myCard v-for="(film,index) in FilmList" :key="index" :film="film"/>
                        <myCard v-for="serie in SeriesList" :key="serie.id" :SeriesList="series"/>

        </div>
    </main>
</template>

<script>

    import myCard from "./myCard.vue"

    export default {
        name: "myMain",
        components:{
            myCard
        },
        props:["FilmList", "SeriesList"]
    }
</script>

<style scoped lang="scss">
    main{
        background-color: grey;
    }

    .card-container{
        display: flex;
        justify-content: center;
        flex-wrap: wrap;
    }

     h1{
        width: 100%;
        margin: 20px;
        text-align: center;
    }
</style>