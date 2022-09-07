<template>
    <main class="main-content">
        <div class="container">
            <div v-for="(card, index) in dischi" :key="index" class="col">
                <Card :card="card"/>
            </div>
        </div>
    </main>
</template>

<script>
import Card from './CardComponent.vue';

export default {
    data() {
        return {
            dischi: [],
        }
    },
    components: {
        Card
    },
    created() {
        this.axios
                .get('https://flynn.boolean.careers/exercises/api/array/music')
                .then((res) => {
                    this.dischi = res.data.response;
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