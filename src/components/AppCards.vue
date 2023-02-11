<script>
        export default{
                namne:"appCards",
                props:{
                        x : Object,
                },
                computed:{
                        flag(){
                                let lang = this.x.original_language;

                                switch(lang){
                                        case "en":
                                                lang = "gb";
                                                break;
                                        case"ja":
                                                lang = "jp";
                                                break;
                                }
                                const flag = "https://www.countryflagicons.com/FLAT/16/"+ lang.toUpperCase()+".png"
                                return flag
                        },
                        coverCard(){
                                const imagine = "https://image.tmdb.org/t/p/w342" + this.x.poster_path
                                return imagine
                        },
                        vote(){
                                let newVoto = this.x.vote_average;
                                const vote = Math.ceil( newVoto / 2) ;
                                return vote;
                        }
                        
                                
                        
                }
        }
</script>

<template>

  <div class="col-sm-3 mb-3 mb-sm-0 ">
    <div class="card text-bg-darck">
      <div class="card-body ">
        <img :src="coverCard" class="card-img">
                <div class="card-img-overlay text-light ">
                        <h2 class="card-title">Titolo {{x.name || x.title }}</h2>
                        <p class="card-text">Titolo Originale {{x.original_name || x.original_title }}.</p>

                        <div> Lingua : {{ x.original_language }} <img :src="flag" ></div>
                        <p>voto: <span v-for="star in vote" class="text-danger" >
                                        <font-awesome-icon icon="fa-solid fa-star" />  
                                </span>
                                <span v-for="star in (5 - vote)">
                                        <font-awesome-icon icon="fa-regular fa-star" /> 
                                </span>
                        </p>
                        <p>Overview: {{ x.overview }}</p>

                       
                </div>
      </div>
    </div>
  </div>








</template>

<style lang="scss" scoped>

</style>