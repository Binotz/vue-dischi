<template>
  <div class="search">
    <!-- Genre selector -->
    <select name="genre" id="genreList" v-model="selectedGenre" @change="filterGenre">
        <option v-for="(genre,index) in genreList" :key="index" :value="genre" > 
            {{ genre }}
        </option>
    </select>
    <!-- author selector -->
    <select name="author" id="authorList" v-model="selectedAuthor" @change="filterGenre">
        <option v-for="(author,index) in authorList" :key="index" :value="author" > 
            {{ author }}
        </option>
    </select>
    <!-- <button @click="filterGenre">Seleziona</button> -->
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
            authorList: [],
            selectedGenre: 'All',
            selectedAuthor: 'All',
        }
    },
    methods:{
        filterGenre: function(){
            this.$emit('genreFilterEmit', this.selectedGenre);
            this.$emit('authorFilterEmit', this.selectedAuthor);
        }
    },
    mounted(){
        //Genre list generator without duplicates
        this.genreList.push('All');
        this.albums.forEach(album =>{
            if(!this.genreList.includes(album.genre)){
                this.genreList.push(album.genre);
            }
        });
        //author list generator without duplicates
        this.authorList.push('All');
        this.albums.forEach(album =>{
            if(!this.authorList.includes(album.author)){
                this.authorList.push(album.author);
            }
        });
        console.log('mounted')
    },
    watch:{
        //dropdown menu update when a genre is selected
        albums: function(){
            this.authorList = [];
            this.authorList.push('All');
            this.albums.forEach(album =>{
                if(!this.authorList.includes(album.author)){
                    this.authorList.push(album.author);
                }
            });
        }
    }
}
</script>

<style lang="scss" scoped>

.search{
    display: flex;
    justify-content: center;
    margin-bottom: 1rem;
    select{
        margin-right: 1rem;
    }
}
</style>
