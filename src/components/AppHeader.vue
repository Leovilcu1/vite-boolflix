<script>
    import {store} from "../store"
    export default{
        name:"AppHeader",
        data(){
            return{
                store
            }
        }
    }
</script>

<template>
   <header>
    <div>
        <nav class="navbar bg-body-tertiary py-0 fixed-top">
        <div class="container-fluid bg-black py-3">
        <a class="navbar-brand text-danger fs-1">BOOLFLIX</a>
        <form class="d-flex" role="search">
        <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search" v-model="store.inputText" @keyup="$emit('search')">
        </form>
  </div>
</nav>
    </div>
   </header>
</template>


<style lang="scss" scoped>

</style>