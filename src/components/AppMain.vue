<script>

import axios, { Axios } from "axios";
import {store} from "../store"
    export default{
        name:"AppMain",
        data(){
            return{
                store,
                axios,

            }
        },
        methods:{
            getFlag(countri){
                if(countri == "en"){
                    countri = "gb"
                }
                else if(countri == "ja"){
                    countri = "jp"
                }
                const flag = "https://www.countryflagicons.com/FLAT/64/"+countri.toUpperCase()+".png"
                return flag;
                
            },
            getImg(apiImg){
                const imagine = "https://image.tmdb.org/t/p/w342" + apiImg
                return imagine;
            },
            numAro(numb){

                const numero = Math.ceil(numb / 2) ;
                return numero;
            },
            starRegular(star){
                return 5-star
            }
            
        }
    }
</script>

<template>

    <main>
        <div>
            <h1>MOVIES</h1>
            <ul v-for="i, in this.store.movies">
                <img :src=" getImg(i.poster_path)">
                <li> Titolo: {{i.title }}</li> 
                <li> Titolo Originale: {{ i.original_title }}</li>
                <img :src=" getFlag(i.original_language)">
                <li> Lingua : {{ i.original_language }}</li>
                <li> Voto: {{numAro(i.vote_average)}} </li>
                <span  v-for="x in numAro(i.vote_average)"><font-awesome-icon icon="fa-solid fa-star" /> </span>
                <span  v-for="y in starRegular(numAro(i.vote_average))"><i class="fa-regular fa-star"></i> </span>
            </ul>
        </div>
        <div>
            <h1>SERIE-TV</h1>
            <ul v-for="i, in this.store.serieTV">
                <img :src=" getImg(i.poster_path)">
                <li> Titolo: {{i.name }}</li> 
                <li> Titolo Originale: {{ i.original_name }}</li>
                <img :src=" getFlag(i.original_language)">
                <li> Lingua : {{ i.original_language }}</li>
                <li> Voto: {{numAro(i.vote_average)}} </li>
                <span  v-for="x in numAro(i.vote_average)"><font-awesome-icon icon="fa-solid fa-star" /> </span>
                <span  v-for="y in starRegular(numAro(i.vote_average))"><i class="fa-regular fa-star"></i> </span>

            </ul>
        </div>
    </main>

</template>


<style lang="scss" scoped>

</style>