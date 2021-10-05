<template>
<header class="d-flex justify-content-center">
  <div class="logo ">
    <img src="../assets/img/netflix-logo.png" alt="">
  </div>
  <form class="d-flex align-self-center">
    <div>
      <input class="form-control" type="search" placeholder="Cerca il film" id="name" name="name" v-model.trim="needle">
    </div>

    <div>
      <button type="submit" class="btn btn-danger" @click.prevent="$emit('search', needle)">Cerca</button>
    </div>
   
  </form>
</header>  
</template>

<script>  
// import axios from "axios"; 

export default {
  name: 'Searchbar',
  props: [],

  data(){
    return {
      needle:"",
    }
  },
  computed:{

  },
  mounted(){

  },
  created(){

  },
}


</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import "../style/general.scss";
@import "../style/variabiles.scss";

header{
  height: 60px;
  background-color: $headerColor;

    img{
      height: 100%;
      padding: 5px;
    }
    form{
      vertical-align: middle;
    }   
}


</style>
