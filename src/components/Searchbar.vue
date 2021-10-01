<template>
  <form class="d-flex">
    <div>
      <input class="form-control" type="search" placeholder="Cerca il film" id="name" name="name" v-model.trim="needle">
    </div>

    <div>
      <button type="submit" class="btn btn-primary" @click.prevent="$emit('search', needle)">Cerca</button>
    </div>
   
  </form>
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
  // methods:{
  //   getSearch: function () {
  //     console.log(this.needle)
  //   }
  // }
}


</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
