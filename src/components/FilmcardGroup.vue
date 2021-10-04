<template>   
    <div class="col-3 border card">
        
        <img :src="getImg()" alt="" class="d-none">
        <div class="inside-card">
            <h1 class="fw-bold">{{title_original ? title_original : name_original}}</h1>
            <h3>{{title ? title : name}}</h3>
            <div>
                <!-- inserire img da assets -->
                <img class="flag" :src="(language === 'it') ? 
                'https://upload.wikimedia.org/wikipedia/commons/thumb/0/03/Flag_of_Italy.svg/64px-Flag_of_Italy.svg.png' : 
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

        // getStar: function() {
        //     for (let i = 0; i < Math.round(this.vote); i++) {
                
                
        //     }
        // }
    }

}
</script>

<style>
   img.flag{
        width: 30px;
    }

    .yellow{
        color: yellow;
    }
</style>