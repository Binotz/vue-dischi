<template>
  <div class="search">
    <select name="genre" id="genreList" v-model="selectedGenre">
        <option v-for="(genre,index) in genreList" :key="index" :value="genre.toLowerCase()"> 
            {{ genre }}
        </option>
    </select>
    <button @click="filterGenre">Seleziona</button>
  </div>
</template>

<script>
export default {
    name: "SearchComeponent",
    props: {
        albums: Array,
    },
    data(){
        return{
            genreList: [],
            selectedGenre: 'All'
        }
    },
    methods:{
        filterGenre: function(){
            this.$emit('genreFilterEmit', this.selectedGenre);
        }
    },
    mounted(){
        this.genreList.push('All');
        this.albums.forEach(album =>{
            if(!this.genreList.includes(album.genre)){
                this.genreList.push(album.genre);
            }
        });
    },
}
</script>

<style lang="scss" scoped>

.search{
    color: white;
}
</style>
