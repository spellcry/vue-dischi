<template>
    <header class="main-header">
        <img src="../assets/spotify_logo.png" alt="">
        <div class="filters">
            <div class="filter">
                <label for="filters__genere">Genere</label>
                <select @click="$emit('filterGenere', genere)" v-model="genere" id="filters__genere" class="filter__genere">
                    <option value="1">Tutti</option>
                    <option value="2">Rock</option>
                    <option value="3">Pop</option>
                    <option value="4">Jazz</option>
                    <option value="5">Metal</option>
                </select>
            </div>
        </div>
    </header>
</template>

<script>
export default {
    data() {
        return {
            genere: '1',
        }
    },
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