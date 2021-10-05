<template>   
    <div class="card">
        
        <img v-if="poster" :src="getImg()" alt="" class=" my-card-img">
        <img v-else src="../assets/img/placholder342x458.png" alt="" class=" my-card-img">
        <div class="inside-card ">
            <h1 class="">Titolo: {{title_original ? title_original : name_original}}</h1>
            <h3>Titolo originale: {{title ? title : name}}</h3>
            <div class="voto mb-2">                     
                <i v-for="n in 5" :key="n" class="fas fa-star" :class="(n <= Math.round(vote)/2) ? 'yellow' : 'gray' "></i>   
                <!-- <p>{{vote}}</p>  -->
            </div>
            <div class="language-wrapper">
                <img v-if="language === 'it'" src="../assets/img/64px-Flag_of_Italy.png" alt="Italian flag">
                <img v-else-if="language === 'en'" src="../assets/img/Flag_of_the_United_Kingdom_(3-5).svg.png" alt="England flag">  
                <p v-else>{{language}}</p>         
            </div>
        
            
        </div>         
    </div>  
</template>

<script>

export default {
    name: "FilmcardGroup",
    props: ['title_original','title', "language","vote",
            "name_original", "name",
            "poster"],
    data: function(){
        return {
            
        }
    },
    methods:{
        getImg: function () {
           return  "https://image.tmdb.org/t/p/" + "w342/" + this.poster;
        },
    }

}
</script>

<style  lang="scss">
@import "../style/general.scss";
@import "../style/variabiles.scss";

    .card{
        max-width: 232px;
        max-height: 347px;
        margin: 5px;
       
    }
    .inside-card{
        height: 100%;
        background-color: $bgColorCard;
        color: $cardTextColor;
        padding: 20px;
  
    }
    .my-card-img{
        height: -moz-fit-content;
    }
    .card:not(:hover){
        .inside-card{
            display: none;
        }
    }

    .card:hover{
        border: 3px double rgba(249,0,0,0.68);

        .my-card-img{
            display: none;
        }  
    }
   .language-wrapper img{
        width: 30px;
    }
    .yellow{
        color: orange;
    }
</style>