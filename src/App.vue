<template>
  <div id="app">
    <!-- Header -->
    <header>
      <HeaderComponent />
    </header>
    <!-- Main -->
    <main>
      <LoadingComponent v-if="albumsFromAPI === null"/>
      <MainComponent :albums="albumsFromAPI" v-else/>
    </main>
  </div>
</template>



<script>
import HeaderComponent from './components/HeaderComponent.vue';
import MainComponent from './components/MainComponent.vue';
import LoadingComponent from './components/LoadingComponent.vue';
import axios from "axios"

export default {
  name: 'App',
  components: {
    HeaderComponent,
    MainComponent,
    LoadingComponent,
},
  data(){
    return{
      albumsFromAPI: null
    }
  },
  methods:{},
  mounted(){
    axios.get('https://flynn.boolean.careers/exercises/api/array/music')
    .then( resp => {
      setTimeout(()=>{
        this.albumsFromAPI = resp.data.response;
      },1000);
    });
  }
}
</script>



<style lang="scss">
@import '@/assets/style/variables.scss';
@import "~@fontsource/montserrat/index.css";

*{
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
body{
  background-color: $primary-color;
}
#app {
  font-family: "Montserrat",sans-serif;
}
</style>
