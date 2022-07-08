<template>
  <div class="loader">
    <h2>
        Caricamento...
    </h2>
  </div>
</template>

<script>
export default {
    name: "LoadingComponent"
}
</script>

<style lang="scss" scoped>
.loader{
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100%;
}
h2{
    color: white;
    font-size: 100px;
    font-weight: bold;
}

</style>
