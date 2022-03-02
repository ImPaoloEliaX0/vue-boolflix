<template>
  <header>
    <!-- logo netflix-->
    <img src="https://www.edigitalagency.com.au/wp-content/uploads/Netflix-logo-red-black-png.png" alt="Logo di netflix">

<!-- barra di ricerca per trovare i titoli dei film-->
    <div class="search">
      <input type="text" v-model="titleText" @keyup.enter="SearchFilm">

<!-- chiamo la funzione searchfilm premendo il bottone-->
      <button @click="SearchFilm">Search for films</button>
    </div>

  </header>

</template>

<script>
  export default {
    name: 'myHeader',
    data(){
      return{
        titleText: ""
      }
    },
    /* uso la emit per richiamare la funzione di ricerca in App.vue*/
    methods: {
      SearchFilm(){
        this.$emit("CallServer", this.titleText);
      }
    }
  }
</script>

<!-- Stilizzazione dell'header -->
<style lang="scss">
  header{
    display: flex;
    align-items: center;
    justify-content: space-around;
    height: 80px;
    background-color: rgb(5, 5, 5);
    img{
      height: 70%;
      margin-right: 305px;
    }
  }
</style>
