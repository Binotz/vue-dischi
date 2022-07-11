<template>
  <section class="container">
    <SearchComponent :albums="filteredAlbums" 
    @genreFilterEmit="filterAlbums"
    @authorFilterEmit="filterAuthor"
    />
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
            genreSelected: 'All',
            authorSelected: 'All'
        }
    },
    methods:{
        filterAlbums: function(genre){
            this.genreSelected = genre;
        },    
        filterAuthor: function(author){
            this.authorSelected = author;
        }
    },
    computed:{
        filteredAlbums: function(){
            if(this.genreSelected === 'All' && this.authorSelected === 'All'){
                return this.albums;
            } 
            return this.albums.filter((album)=>{
                if(this.genreSelected !== 'All' && this.authorSelected === 'All'){
                    return album.genre === this.genreSelected;
                }
                if(this.authorSelected !== 'All' && this.genreSelected === 'All'){
                    return album.author === this.authorSelected;
                }
                if(this.genreSelected !== 'All' && this.authorSelected !== 'All'){
                    return album.genre === this.genreSelected && album.author === this.authorSelected;
                }
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
