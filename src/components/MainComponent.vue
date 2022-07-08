<template>
  <section class="container">
    <CardsListComponent :albums="albums"/>
  </section>
</template>

<script>
import CardsListComponent from './CardsListComponent.vue'

export default {
    name: "MainComponent",
    components:{
        CardsListComponent
    },  
    props:{
        albums: Array
    }
}
</script>

<style lang="scss" scoped>
    .container{
        padding: 4rem;
        width: 70%;
        margin: 0 auto;
    }
</style>
