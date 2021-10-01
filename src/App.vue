<template>
  <div>
   
    <Searchbar @search="SearchFilm"/>
   
  </div>
</template>

<script>
import Searchbar from './components/Searchbar.vue';
import axios from "axios";

export default {
  name: 'App',
  data: function (){
    return {
      filmList: [],
    }
  },
  components: {
    Searchbar
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
