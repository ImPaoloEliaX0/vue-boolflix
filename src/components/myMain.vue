<template>
    <main>
        <!-- creo due cicli for per mostrare prima i film e poi le serie -->
        <div class="card-container">
            <myCard v-for="(film,index) in FilmList" :key="index" :film="film"/>
                        <myCard v-for="serie in SeriesList" :key="serie.id" :SeriesList="series"/>

        </div>
    </main>
</template>

<script>
/* importo il componente mycard.vue */

    import myCard from "./myCard.vue"

    export default {
        name: "myMain",
        components:{
            myCard
        },
        /*utilizzo le props per richiamare i due array dall'elemento padre */
        props:["FilmList", "SeriesList"]
    }
</script>

<!-- stilizzazione del main e dei container degli elementi -->

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