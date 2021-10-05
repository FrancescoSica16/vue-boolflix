<template>   
    <div class="col-3 card">
        
        <img :src="getImg()" alt="" class=" my-card-img img-fluid">

        <div class="inside-card">
            <h1 class="fw-bold">{{title_original ? title_original : name_original}}</h1>
            <h3>{{title ? title : name}}</h3>
            <div>
                <!-- inserire img da assets -->
                <img class="flag" :src="(language === 'it') ? 
                require('../assets/img/64px-Flag_of_Italy.png') : 
                (language === 'en') ?
                'https://upload.wikimedia.org/wikipedia/commons/thumb/8/83/Flag_of_the_United_Kingdom_%283-5%29.svg/64px-Flag_of_the_United_Kingdom_%283-5%29.svg.png' : 
                // else
                'https://upload.wikimedia.org/wikipedia/commons/thumb/7/72/Flag_of_Union_of_Soviet_Socialist_Republics.png/64px-Flag_of_Union_of_Soviet_Socialist_Republics.png'" alt="">
            </div>
            <!-- <p>{{vote}}</p> -->
            <div class="voto">
                <p>{{vote}}</p>
                <i v-for="n in 5" :key="n" class="fas fa-star" :class="(n <= Math.round(vote)/2) ? 'yellow' : 'gray' "></i>
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
    }
    .card:not(:hover){
        .inside-card{
            display: none;
        }
    }

    .card:hover{
        .my-card-img{
            display: none;
        }  
    }

   img.flag{
        width: 30px;
    }

    .yellow{
        color: yellow;
    }
</style>