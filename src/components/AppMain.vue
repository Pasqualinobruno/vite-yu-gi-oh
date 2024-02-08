<script>
import axios from 'axios';
import AppCard from './AppCard.vue';
export default {
    name: 'AppMain',
    data() {
        return {
            base_api_url: 'https://db.ygoprodeck.com/api/v7/cardinfo.php?num=40&offset=0&fname=Sky_striker',
            cards: null,
            error: false,
        }
    },
    components: {
        AppCard,
    },
    mounted() {
        axios
            .get(this.base_api_url)
            .then((response, index) => {
                /*  console.log(response); importa i nostri file */
                /* console.log(response.data); importa il data(l'array) e il meta  */
                console.log(response.data.data);//importa solo l'array
                this.cards = response.data.data;
                /* console.log(this.cards[0]);//questo logga il singolo elemento */
                /* console.log(this.cards[0].card_images[0].image_url);//la singola immagine di un singolo elemento */

            })
            .catch((error) => {
                console.error(error);
            })
    }
}
</script>
<template>
    <main>
        <div class="sezion">
            <select name="archetypses" id="archetype">
                <option selected value="all">All</option>
                <option value="alien">Alien</option>
            </select>
        </div>
        <div class="container">
            <div class="number_cards">Found 39 cards</div>
            <div class="row">
                <AppCard v-for="(card, index) in cards" :key="index" :card="card"></AppCard>
            </div>
        </div>
    </main>
</template>
<style scoped>
.sezion {
    width: 70%;
    max-width: 1176px;
    margin: auto;

    & select {
        padding: 0.2rem;
        padding-right: 1rem;
        margin: 0.5rem;
        border-radius: 0.3rem;
    }
}


main {
    & .container {
        background-color: var(--yu-gi-oh-light);
        padding: 1rem;

        & .number_cards {
            background-color: var(--yu-gi-oh-dark);
            padding: 0.5rem;
            color: var(--yu-gi-oh-light);
        }




    }



}
</style>