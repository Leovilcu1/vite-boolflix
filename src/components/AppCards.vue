<script>
import { remove } from '@vue/shared';

        export default{
                namne:"appCards",
                data(){
                        return{
                                hover:false,
                        }
                },
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
                        },    
                }
        }
</script>

<template>

  <div class="col-sm-3 mb-3 mb-sm-0 hover-overlay  div" @mouseenter="hover = true" @mouseleave = "hover = false" :class ="{'div-hover' : hover}" >
    <div class="card text-bg-darck border-0 m-2 leo">
      <div class="">
        <img :src="coverCard" class="card-img img-thumbnail cover w-100  p-0 border-0">
                <div class="card-img-overlay text-light overflow-auto text-center bg-dark bg-opacity-75 " v-if ='hover'>
                        <p class="card-title">Titolo : {{x.name || x.title }}</p>
                        <p class="card-text">Titolo Originale : {{x.original_name || x.original_title }}.</p>

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