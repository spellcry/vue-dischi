<template>
  <div id="app">
    <MainHeader @filterGenere="getGenere"/>
    <MainContent :genere="genere"/>
  </div>
</template>

<script>
import MainHeader from './components/HeaderComponent.vue'
import MainContent from './components/MainContent.vue'

export default {
  name: 'App',
  components: {
    MainHeader,
    MainContent,
  },
  data() {
    return {
      genere: '1',
    }
  },
  methods: {
    getGenere(genere) {
      this.genere = genere;
      
    },
  }
}
</script>

<style lang="scss">
  @import './styles/general.scss';
  @import './styles/variables';

  #app {
    display: flex;
    flex-direction: column;
    height: 100vh;
    font-family: $font-family;
  }
</style>
