<template>
    <main class="main-content">
        <div class="container">
            <div v-for="(card, index) in dischiFiltrati" :key="index" class="col">
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
    computed: {
        dischiFiltrati() {
            return this.dischi.filter((disco) => {
                let genreText;
                switch (this.genere) {
                    case '1':
                        genreText = '';
                        break;
                    case '2':
                        genreText = 'Rock';
                        break;
                    case '3':
                        genreText = 'Pop';
                        break;
                    case '4':
                        genreText = 'Jazz';
                        break;
                    case '5':
                        genreText = 'Metal';
                        break;
                }
                console.log(this.genere);
                return disco.genre.includes(genreText);                
            });
        }
    },
    props: {
        genere: {
            type: String,
            default: ''
        },
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