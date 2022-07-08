<template>
  <nav>
    <img src="@/assets/img/logo.png" alt="Logo">
  </nav>
</template>

<script>
export default {
    name:"HeaderComponent",
}
</script>

<style lang="scss" scoped>
@import '@/assets/style/variables.scss';
nav{
    background-color: $secondary_color;
    img{
        width: 80px;
        padding: .5rem;
    }
}
</style>
