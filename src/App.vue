<template>
  <div id="app">
    
    <myHeader @SearchFilm="CallServer" />
    <myMain :FilmList="FilmList" />
  </div>
</template>

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
    
    return{
      api_key:"b6284a4c041c4eee701987532793f7f9",
      FilmList: [],
      SeriesList: [],
      
    }
  },
  methods:{
       CallServer(Input){
      
      this.CallSfilm(Input);
      this.CallSeries(Input);
      
    },
    CallSFilm(Input){
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