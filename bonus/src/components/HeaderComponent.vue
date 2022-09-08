<template>
    <header class="main-header">
        <img src="../assets/spotify_logo.png" alt="">
        <div class="filters">
            <div class="filter">
                <label for="filter__genere">Genere</label>
                <select @change="$emit('filterGenere', genere); setAuthorSelect();" v-model="genere" id="filter__genere" class="filter__genere">
                    <option value="1">Tutti</option>
                    <option value="2">Rock</option>
                    <option value="3">Pop</option>
                    <option value="4">Jazz</option>
                    <option value="5">Metal</option>
                </select>
            </div>
            <div class="filter">
                <label for="filter_author">Artista</label>
                <select @change="$emit('filterAuthor', author)" v-model="author" id="filter_author" class="filter__author">
                    <option value="Tutti">Tutti</option>
                    <option v-for="(disk, index) in filteredDisk" :key="index" :value="disk.author">{{ disk.author }}</option>
                </select>
            </div>
        </div>
    </header>
</template>

<script>
export default {
    props: {
        filteredDisk: Array,
    },
    data() {
        return {
            genere: '1',
            author: 'Tutti',
        }
    },
    methods: {
        setAuthorSelect() {
            if ( this.genere === '1' )
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