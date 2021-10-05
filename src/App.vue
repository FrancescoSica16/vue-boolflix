<template>
  <div>
    <Searchbar @search="SearchFilm"/>
    
    <div class="container">
      <div class="row">
        <div class="col-12 text-center">
          <h1 v-if="filmList.length > 0">Film</h1> 
        </div>
      </div>  

    <div class="row">     
      <div class="col d-flex flex-wrap justify-content-center">
        <FilmcardGroup v-for="(film) in filmList" :key="film.id" 
        :poster="film.poster_path"
        :title_original="film.original_title" :title="film.title" :language="film.original_language" :vote="film.vote_average"/>     
      </div>     
    </div>
    

    <div class="row">
      <div class="col-12 text-center">
        <h1 v-if="serieList.length > 0">Serie TV</h1>
      </div>
    </div>

    <div class="row">
      <div class="col d-flex flex-wrap justify-content-center">      
          <FilmcardGroup v-for="(serie, index) in serieList" :key="index" 
          :name_original="serie.original_name" :name="serie.name" :poster="serie.poster_path"
          :title_original="serie.original_title" :title="serie.title" :language="serie.original_language" :vote="serie.vote_average"/>          
      </div>
    </div>
    
    </div>
  </div>
</template>

<script>
import Searchbar from './components/Searchbar.vue';
import FilmcardGroup from "./components/FilmcardGroup.vue";
import axios from "axios";


export default {
  name: 'App',
  data: function (){
    return {
      filmList: [],
      serieList: [],
      key:'3470fd1ace343e7c3044569008e5458d',
    }
  },
  props: {
    "movies": Array,
    "tvSeries":Array
  },
  components: {
    Searchbar,
    FilmcardGroup
  },
  computed:{

  },
  methods:{
    SearchFilm: function (serchKey) {

      axios.get('https://api.themoviedb.org/3/search/movie/', {
        params: { 
          api_key : this.key,
          query: serchKey
        }})
      .then( (response) => {
         this.filmList = response.data.results.slice();
        console.log(this.filmList);

           this.filmList.forEach(element => {
           axios.get("https://api.themoviedb.org/3/movie/"+ element.id +"/casts",{
             params: { 
                api_key : this.key,
            
           }
        });
    });

    }); //fine end 73 response

    axios.get('https://api.themoviedb.org/3/search/tv/', {
        params: { 
          api_key : this.key,
          query: serchKey
        }})
      .then( (response) => {
         this.serieList = response.data.results.slice();
          console.log(this.serieList);
    });
    }
  }
}
</script> 

<style lang="scss">
@import "style/general.scss";
@import "style/variabiles.scss";

body{
  background-color: $bodyColor;
}

</style>
