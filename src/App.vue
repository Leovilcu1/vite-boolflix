<script>  
  import {store} from "./store";
  import axios from 'axios';
  import AppHeader from './components/AppHeader.vue';
  import AppMain from './components/AppMain.vue';
import { generate } from "@vue/compiler-core";
  export default{
    name:"App",
    components:{
      AppHeader,
      AppMain
    },
    data(){
      return{
        store
      }
    },
    methods:{
      getChiamataApi(){
        this.sceltaGenereMovie("movie");
        this.sceltaGenereMovie("tv");
      },
      sceltaGenereMovie(x){
        let url = "https://api.themoviedb.org/3/search/";
        axios
          .get(url + x,{
            params:{
              api_key:"8c2d4c1e76de07b27d59c572475eb1ed",
              language:"it-IT",
              query:this.store.inputText,
            }//params
          })//.get
          .then((response) =>{
            if(x == "movie"){
              this.store.movies = response.data.results
            }
            else{
              this.store.serieTV = response.data.results
            }
          })
      }
    },
  };
</script>

<template>
  <AppHeader @search = "getChiamataApi" />
  <AppMain/>
  
</template>

<style lang="scss">
  @use "./styles/main.scss" as *;
</style>
