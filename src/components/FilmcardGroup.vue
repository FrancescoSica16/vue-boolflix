<template>   
    <div class="col-3 border">
        <h1>{{title_original}}</h1>
        <h3>{{title}}</h3>
        <div>
            <!-- inserire img da assets -->
            <img class="flag" :src="(language === 'it') ? 
            'https://upload.wikimedia.org/wikipedia/commons/thumb/0/03/Flag_of_Italy.svg/64px-Flag_of_Italy.svg.png' : 
            (language === 'en') ?
            'https://upload.wikimedia.org/wikipedia/commons/thumb/8/83/Flag_of_the_United_Kingdom_%283-5%29.svg/64px-Flag_of_the_United_Kingdom_%283-5%29.svg.png' : 
            // else
            'https://upload.wikimedia.org/wikipedia/commons/thumb/7/72/Flag_of_Union_of_Soviet_Socialist_Republics.png/64px-Flag_of_Union_of_Soviet_Socialist_Republics.png'" alt="">
        </div>
        <p>{{vote}}</p>         
    </div>
      
    

    
</template>

<script>
export default {
    name: "FilmcardGroup",
    props: ['title_original','title', "language","vote"],

}
</script>

<style>
   img.flag{
        width: 30px;
    }
</style>