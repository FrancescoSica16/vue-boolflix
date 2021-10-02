<template>
    <div class="container">
      <div class="row">
        <div class="col-3 ">
        <h1>{{title_original}}</h1>
        <h3>{{title}}</h3>
        <p>{{language}}</p>
        <p>{{vote}}</p>         
        </div>
      </div>
    </div>

    
</template>

<script>
export default {
    name: "FilmcardGroup",
    props: ['title_original','title', "language","vote"],

}
</script>

<style>

</style>