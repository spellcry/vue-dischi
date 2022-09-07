<template>
    <main class="main-content">
        <template v-if="!isLoaded">
            <LoaderComponent/>
        </template>
        <div v-if="isLoaded" class="container">
            <div v-for="(card, index) in dischi" :key="index" class="col">
                <Card :card="card"/>
            </div>
        </div>
    </main>
</template>

<script>
import Card from './CardComponent.vue';
import LoaderComponent from './LoaderComponent.vue';

export default {
    data() {
        return {
            dischi: [],
            isLoaded: false,
        }
    },
    components: {
        Card,
        LoaderComponent,
    },
    created() {
        this.axios
                .get('https://flynn.boolean.careers/exercises/api/array/music')
                .then((res) => {
                    this.dischi = res.data.response;
                })
                .finally(() => {
                    this.isLoaded = true;
                });
    }
}
</script>

<style lang="scss" scoped>
    @import '../styles/variables';

    .main-content {
        display: flex;
        align-items: center;
        flex-grow: 1;
        background-color: $dark-grey;
        .container {
            display: flex;
            flex-wrap: wrap;
            gap: $gap;
            max-width: 1200px;
            margin-inline: auto;
            .col {
                flex-basis: calc(calc(100% - calc($gap * 4)) / 5);
            }
        }
    }
</style>