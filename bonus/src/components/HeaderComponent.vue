<template>
    <header class="main-header">
        <img src="../assets/spotify_logo.png" alt="">
        <div class="filters">
            <div class="filter">
                <label for="filter__genere">Genere</label>
                <select @change="$emit('filterGenere', genere); setAuthorSelect();" v-model="genere" id="filter__genere" class="filter__genere">
                    <option value="Tutti">Tutti</option>
                    <option v-for="(genre, index) in genreList" :key="index" :value="genre">{{ genre }}</option>
                </select>
            </div>
            <div class="filter">
                <label for="filter_author">Artista</label>
                <select @change="$emit('filterAuthor', author)" v-model="author" id="filter_author" class="filter__author">
                    <option value="Tutti">Tutti</option>
                    <option v-for="(author, index) in authorList" :key="index" :value="author">{{ author }}</option>
                </select>
            </div>
        </div>
    </header>
</template>

<script>
export default {
    props: {
        genreList: Array,
        authorList: Array,
    },
    data() {
        return {
            genere: 'Tutti',
            author: 'Tutti',
        }
    },
    methods: {
        setAuthorSelect() {
            this.author = 'Tutti';
        }
    }
}
</script>

<style lang="scss" scoped>
    @import '../styles/variables';

    .main-header {
        display: flex;
        align-items: center;
        padding: 0.6rem 1rem;
        background-color: $light-grey;
        img {
            max-width: 50px;
            margin-right: auto;
        }
        .filters {
            display: flex;
            gap: 2rem;
        }
    }
</style>