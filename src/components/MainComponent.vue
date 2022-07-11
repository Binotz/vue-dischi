<template>
  <section class="container">
    <SearchComponent :albums="albums" 
    @genreFilterEmit="filterAlbums"/>
    <CardsListComponent :albums="filteredAlbums"/>
  </section>
</template>

<script>
import CardsListComponent from './CardsListComponent.vue'
import SearchComponent from './SearchComponent.vue'

export default {
    name: "MainComponent",
    components:{
        CardsListComponent,
        SearchComponent
    },  
    props:{
        albums: Array,
    },
    data(){
        return {
            genreSelected: 'All'
        }
    },
    methods:{
        filterAlbums: function(genre){
            this.genreSelected = genre.charAt(0).toUpperCase() + genre.slice(1);
        }        
    },
    computed:{
        filteredAlbums: function(){
            if(this.genreSelected === 'All'){
                return this.albums;
            }
            return this.albums.filter((album)=>{
                return album.genre === this.genreSelected;
            });
        }
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
