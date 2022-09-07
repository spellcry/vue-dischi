<template>
    <div class="card">
        <img :src="card.poster" alt="" class="card__img">
        <div class="card__description">
            <h4 class="title">{{ card.title }}</h4>
            <div class="author-year">
                <p class="author">{{ card.author }}</p>
                <p class="year">{{ card.year }}</p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        card: Object,
    }
}
</script>

<style lang="scss" scoped>
    @import '../styles/variables';

    .card {
        height: 100%;
        padding: 1rem;
        background-color: $light-grey;
        box-shadow: -3px 3px 10px rgba(255, 255, 255, 0);
        transition: all 200ms ease-in-out;
        cursor: pointer;
        &:hover {
            transform: scale(1.03);
            box-shadow: -3px 3px 10px rgba(255, 255, 255, 0.4);
        }
        .card__img {
            margin-bottom: $gap-description;
            aspect-ratio: 1;
        }
        .card__description {
            display: flex;
            flex-direction: column;
            align-items: center;
            text-align: center;            
            .title {
                margin-bottom: $gap-description;
                font-size: 1.5rem;
                color: $white;
                text-transform: uppercase;
            }
            .author,
            .year {
                color: $text-dark;
            }
            .author {
                font-size: 1.1rem;
            }
            .year {
                font-size: 0.9rem;
            }
        }
    }
</style>