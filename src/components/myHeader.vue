<template>
  <header>
    <img src="https://www.edigitalagency.com.au/wp-content/uploads/Netflix-logo-red-black-png.png" alt="Logo di netflix">

    <div class="search">
      <input type="text" v-model="titleText" @keyup.enter="SearchFilm">

      <button @click="CallServer">Search for films</button>
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
    methods: {
      SearchFilm(){
        this.$emit("CallServer", this.titleText);
      }
    }
  }
</script>

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
