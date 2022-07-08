<template>
    <div class="card-list-layout">
        <SingleCardComponent 
            v-for="album in albums" 
            :key="album.id" 
            :album="album"
        />
    </div>
</template>



<script>
import SingleCardComponent from './SingleCardComponent.vue'

export default {
    name:"CardsListComponent",
    components:{
        SingleCardComponent
    },
    props:{
        albums: Array
    }
}
</script>



<style lang="scss" scoped>
.card-list-layout{
    display: flex;
    flex-wrap: wrap;
    gap: 30px;
}
</style>
