<script>
import axios from 'axios';
export default {
    name: 'AppMain',
    data() {
        return {
            base_api_url: 'https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0',
            cards: null,
            error: false,

        }
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
        <div class="container">
            <select name="archetypses" id="archetype">
                <option selected value="all">All</option>
                <option value="alien">Alien</option>

            </select>
            <div class="number_cards">Found 39 cards</div>


            <div class="row">
                <div class="col-12 col-sm-6 col-md-3 col-lg-5 col-xl-5" v-for="(card, index) in cards" :key="index">
                    <div class="card">
                        <img :src="card.card_images[0].image_url" alt="Card Image">
                        <div class="info_card">
                            <p class="name">{{ card.name }}</p>
                            <p class="archetype">{{ card.archetype }}</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </main>
</template>
<style scoped>
main {
    >.container {
        background-color: var(--yu-gi-oh-light);
        padding: 1rem;

        >select {
            padding: 0.2rem;
            padding-right: 1rem;
            margin: 0.5rem;
            border-radius: 0.3rem;
        }

        & .number_cards {
            background-color: var(--yu-gi-oh-dark);
            padding: 0.5rem;
            color: var(--yu-gi-oh-light);
        }

        & .card {
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




    }





}
</style>