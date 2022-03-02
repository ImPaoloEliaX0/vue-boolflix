<template>
  <div id="app">
    
    <!-- all'evento search film chiamo la funzione call server -->
    <myHeader @SearchFilm="CallServer" />
    <myMain :FilmList="FilmList" />
  </div>
</template>

    <!--Importazione componenti-->

<script>
import myHeader from './components/myHeader.vue'
import myMain from './components/myMain.vue'
export default {
  name: 'App',
  components: {
    myHeader,
    myMain
  },
  data(){
    /* Creo due array per inserire i film e le serie tv */
    return{
      api_key:"b6284a4c041c4eee701987532793f7f9",
      FilmList: [],
      SeriesList: [],
      
    }
  },
  /* uso la funzione call server per chiamare separatamente i film e le serie */
  methods:{
       CallServer(Input){
      
      this.CallSfilm(Input);
      this.CallSeries(Input);
      
    },
    
    CallSFilm(Input){
      /* Chiamata axios per inserire gli elementi dei film negli array */
      const axios = require("axios");
      axios.get("https://api.themoviedb.org/3/search/movie", {
        params:{
          api_key: this.api_key,
          query: Input
        }
      }).then( answer => {
        this.FilmList = answer.data.results;
        console.log(this.FilmList);
      })
    },
          /* Chiamata axios per inserire gli elementi delle serie tv negli array */

      CallSeries(Input){
              const axios = require("axios");
      axios.get("https://api.themoviedb.org/3/search/tv", {
        params:{
          api_key: this.api_key,
          query: Input
        }
      }).then( answer => {
        this.SeriesList = answer.data.results;
        console.log(this.SeriesList);
      })

  }
}
}

</script>

<!-- Stilizzazione elementi generali / body -->
<style lang="scss">
  *{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  body{
    background-color: rgb(122, 121, 121);
  }
</style>