npm<template>
<!-- container generale della card-->
    <div class="card">
        <!-- richiamo dinamicamente le immagini accedendo al path fornito dal server-->
        <img :src="Imgslink + film.poster_path" alt="">
        <div class="overlay"></div>
<!-- definisco titolo e informazioni del film -->
        <div class="card-info">
            <h1>{{film.title}}</h1>
            <h2>{{film.original_title}}</h2>
            <lang-flag class="language" :iso="film.original_language"/>
            <p class="vote">{{film.vote_average}}</p>
        </div>
        <!-- Creo due cicli for per mostrare le stelle piene e quelle vuote-->
             <div v-if="film.vote_average != 0">
                <i v-for="(star, index) in Math.ceil(item.vote_average / 2)" :key="index" class="fas fa-star"></i> 
                 <i v-for="(star, index) in 5 - Math.ceil(item.vote_average / 2)" :key="index" class="fa-regular fa-star"></i> 
                 </div>
    </div>
</template>

<script>
/* importo il componente per le bandiere della nazionalità */
    import LangFlag from 'vue-lang-code-flags';

    export default {
        name: "myCard",
        data(){
            return{
                Imgslink: "https://image.tmdb.org/t/p/w342"  
            }
        },
        components: {
            LangFlag
        },
        props: ["film"]
    }
</script>

<!-- stilizzazione singola card film/serie tv -->
<style scoped lang="scss">
    .card{
        margin: 16px;
        text-align: center;
        position: relative;

        .card-info, .overlay{
            display: none;
        }

        .overlay{
            position: absolute;
            background-color: rgba(5, 5, 5, 0.5);
            top: 0;
            right: 0;
            left: 0;
            bottom: 6px;
        }

        &:hover .card-info,
        
         &:hover .overlay{
            display: block;
            cursor: pointer;
        }

        h1,h2,p, .language{
            font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
            color: rgb(245, 240, 240);
            position: absolute;
            left: 50%;
            width: 100%;
            transform: translate(-50%, 0);
        }
    
        h1{
            top: 20px;
        }

        h2{
            top: 200px;
        }
        p.language, .language{
            top: 310px;
        }
        .language{
            width: 50px;
            height: 30px;
            background-size: cover;
        }
        p.vote{
            top: 400px;
        }
          p.overview{
            top: 280px;
            padding: 15px;
            text-align: left;
        }
    }
</style>