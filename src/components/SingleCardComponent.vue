<template>
  <div class="card-layout">
    <div class="card-content">
        <img :src="album.poster" :alt="album.title">
        <h2>{{ album.title.toUpperCase() }}</h2>
        <h3>{{ album. author}}</h3>
        <h4>{{ album.year }}</h4>
    </div>
  </div>
</template>

<script>
export default {
    name: "SingleCardComponent",
    props:{
        album: Object
    },
}
</script>

<style lang="scss" scoped>
@import '@/assets/style/variables.scss';


.card-layout{
    padding: 1.5rem;
    width: calc(20% - 30px);
    background-color: $secondary_color;
}
.card-content{
    display: flex;
    flex-direction: column;
    align-items: center;
    
    img{
        width: 100%;
        display: block;
        margin-bottom: 20px;
    }
    h2{
        color: white;
        text-align: center;
        margin-bottom: 25px;
    }
    h3,h4{
        color: gray;
    }
}
</style>
