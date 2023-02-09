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
        <input type="text" v-model="store.inputText">
        <button @click="$emit('search')"> Cerca</button>
    </div>
   </header>

</template>


<style lang="scss" scoped>

</style>