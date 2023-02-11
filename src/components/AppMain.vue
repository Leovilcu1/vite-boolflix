<script>
import AppCards from "./AppCards.vue";
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
         
        components:{
            AppCards
        },
       
    }
</script>

<template  >    
    
    <main >
        <div class="container">
            <div class="row" >
            <h1>MOVIES</h1>
            <AppCards v-for="i in store.movies" :x ="i"/>
        </div>
        <div class="row">
            <h1>SERIE-TV</h1>
            <AppCards v-for="i in store.serieTV" :x ="i"/>
        </div>
        </div>


        
    </main>

</template>


<style lang="scss" scoped>

</style>