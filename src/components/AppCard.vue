<script>
export default {
    name: 'AppCard',
    data() {
        return {

        }
    },
    props: {
        card: Object
    }
}
</script>

<template>
    <div class="col-12 col-sm-6 col-md-3 col-lg-5 col-xl-5">
        <div class="card">
            <img :src="card.card_images[0].image_url" alt="Card Image">
            <div class="info_card">
                <p class="name">{{ card.name }}</p>
                <p class="archetype">{{ card.archetype }}</p>
            </div>
        </div>
    </div>
</template>

<style scoped>
.card {
    background-color: var(--yu-gi-oh-primary);

    & .info_card {
        padding: 1rem;
        text-align: center;

        & .name {
            padding-bottom: 0.5rem;
            color: var(--yu-gi-oh-light);
            font-size: medium
        }

        & .archetype {
            color: var(--yu-gi-oh-dark);
        }
    }
}
</style>