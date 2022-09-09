<template>
    <main class="main-content">
        <div class="container">
            <div v-for="(card, index) in dischiFiltratiPerAutore" :key="index" class="col">
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
        genreList() {
            let genreArray = [];
            this.dischi.forEach((disco) => {
                if ( !genreArray.includes(disco.genre) )
                    genreArray.push(disco.genre);
            });
            return genreArray.sort((genre1, genre2) => {
                const gen1 = genre1.toLowerCase();
                const gen2 = genre2.toLowerCase();
                return gen1 < gen2 ? -1 : gen1 > gen2 ? 1 : 0;
            });
        },
        authorList() {
            let authorArray = [];
            this.dischiFiltrati.forEach((disco) => {
                if ( !authorArray.includes(disco.author) )
                    authorArray.push(disco.author);
            });
            return authorArray.sort((author1, author2) => {
                const aut1 = author1.toLowerCase();
                const aut2 = author2.toLowerCase();
                return aut1 < aut2 ? -1 : aut1 > aut2 ? 1 : 0;
            });
        },
        dischiAuthorNameFixed() {
            return this.dischi.map((disco) => {
                if ( disco.author === 'Michael Jacjson' )
                    disco.author = 'Michael Jackson'
                return disco;
            });
        },
        dischiFiltrati() {
            return this.dischiAuthorNameFixed.filter((disco) => {
                return this.genere === 'Tutti' ? true : disco.genre.includes(this.genere);                
            })
        },
        dischiFiltratiPerAutore() {
            return this.dischiFiltrati.filter((disco) => {
                return this.author === 'Tutti' ? true : disco.author === this.author;
            });
        }
    },
    props: {
        genere: String,
        author: String,
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
    },
    updated() {
        this.$emit('genreSelected', this.dischiFiltrati);
        this.$emit('genreList', this.genreList);
        this.$emit('authorList', this.authorList);
    },
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
            justify-content: center;
            flex-wrap: wrap;
            gap: $gap;
            flex-basis: 100%;
            max-width: 1200px;
            margin-inline: auto;
            .col {
                flex-basis: calc(calc(100% - calc($gap * 4)) / 5);
            }
        }
    }
</style>