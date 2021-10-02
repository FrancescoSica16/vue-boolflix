<template>
  <div>
   
    <Searchbar @search="SearchFilm"/>

    <div class="d-flex" >
      <FilmcardGroup v-for="(film, index) in filmList" :key="index" 
      :title_original="film.original_title" :title="film.title" :language="film.original_language" :vote="film.vote_average"/>     
    </div>
    

    <!-- <div class="container">
      <div class="row">
        <div class="col-3" v-for="(film, index) in filmList" :key="index">
          <h1>{{film.original_title}}</h1>
          <h3>{{film.title}}</h3>
          <p>{{film.original_language}}</p>
          <p>{{film.vote_average}}</p>

        </div>
      </div>
    </div> -->
    <!-- <h1 v-for="(film, index) in filmList" :key="index">{{film.original_title}}</h1> -->
   
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
    }
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
          api_key : '3470fd1ace343e7c3044569008e5458d',
          query: serchKey
        }})
      .then( (response) => {
         this.filmList = response.data.results.slice();
          console.log(this.filmList);
    })
    }
  },
}
</script> 

<style lang="scss">
@import "style/general.scss";
@import "style/variabiles.scss";

</style>
