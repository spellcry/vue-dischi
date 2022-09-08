<template>
  <div id="app">
    <MainHeader @filterGenere="getGenere" @filterAuthor="getAuthor" :filteredDisk="filteredDisk"/>
    <MainContent @genreSelected="setAuthorFilter" :genere="genere" :author="author"/>
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
      author: 'Tutti',
      filteredDisk: [],
    }
  },
  methods: {
    getGenere(genere) {
      this.genere = genere;
    },
    getAuthor(author) {
      this.author = author;
    },
    setAuthorFilter(dischiFiltrati) {
      this.filteredDisk = dischiFiltrati;
    }
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
