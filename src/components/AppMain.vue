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
                return flag
            }
        }
    }
</script>

<template>

    <main>
        <div>
            <h1>MOVIES</h1>
            <ul v-for="i, in this.store.movies">
                <li >Titolo: {{i.title }}</li> 
                <li >Titolo Originale: {{ i.original_title }}</li>
                <img :src=" getFlag(i.original_language)">
                <li >Lingua : {{ i.original_language }}</li>
                <li >Voto: {{ i.vote_average}}</li>
            </ul>
        </div>
        <div>
            <h1>SERIE-TV</h1>
            <ul v-for="i, in this.store.serieTV">
                <li >Titolo: {{i.name }}</li> 
                <li >Titolo Originale: {{ i.original_name }}</li>
                <img :src=" getFlag(i.original_language)">
                <li >Lingua : {{ i.original_language }}</li>
                <li >Voto: {{ i.vote_average}}</li>
            </ul>
        </div>
    </main>

</template>


<style lang="scss" scoped>

</style>