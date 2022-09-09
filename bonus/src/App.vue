<template>
  <div id="app">
    <MainHeader @filterGenere="getGenere" @filterAuthor="getAuthor" :genreList="genreList" :authorList="authorList"/>
    <MainContent @authorList="setAuthorList" @genreList="setGenreList" @genreSelected="setAuthorFilter" :genere="genere" :author="author"/>
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
      genere: 'Tutti',
      author: 'Tutti',
      filteredDisk: [],
      genreList: [],
      authorList: [],
    }
  },
  methods: {
    getGenere(genere) {
      this.genere = genere;
      this.author = 'Tutti';
    },
    getAuthor(author) {
      this.author = author;
    },
    setAuthorFilter(dischiFiltrati) {
      this.filteredDisk = dischiFiltrati;
    },
    setGenreList(genreList) {
      this.genreList = genreList;
    },
    setAuthorList(authorList) {
      this.authorList = authorList;
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
