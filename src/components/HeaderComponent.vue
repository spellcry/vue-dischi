<template>
    <header class="main-header">
        <img src="../assets/spotify_logo.png" alt="">
    </header>
</template>

<script>
export default {
    
}
</script>

<style lang="scss" scoped>
    @import '../styles/variables';

    .main-header {
        padding: 0.6rem 1rem;
        background-color: $light-grey;
        img {
            max-width: 50px;
        }
    }
</style>