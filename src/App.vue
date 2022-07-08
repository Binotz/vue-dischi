<template>
  <div id="app">
    <!-- Header -->
    <header>
      <HeaderComponent />
    </header>
    <!-- Main -->
    <main>
      <MainComponent />
    </main>
  </div>
</template>



<script>
import HeaderComponent from './components/HeaderComponent.vue';
import MainComponent from './components/MainComponent.vue';

export default {
  name: 'App',
  components: {
    HeaderComponent,
    MainComponent
  }
}
</script>



<style lang="scss">
@import '@/assets/style/variables.scss';
*{
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
#app {
  background-color: $primary-color;
  height: 100vh;
}
</style>
