<template>
<div>
    <div class="wrapper">

        <div class="quote-section">
            <h1 class="quoteText">{{text}}</h1>
            <p class="characterName"><em>--{{character}}</em> </p>
            <h3 class="animeName">{{anime}}</h3>
        </div>

        <div class="buttons">
            <button class="button" v-on:click="setRandomQuote">New Quote!</button>

            <button class="button" v-on:click="toggleFavorite">
                {{buttonText}}
            </button>

        </div>

    </div>
    <!-- <ProductList :products="products" /> -->
</div>
</template>

<script>
// import ProductList from "../components/ProductList.vue"
export default {
    name: 'RandomView',

    data() {
        return {
            random: 1,
            id: 1,
            text: 'There\'s no need to rush. Sometimes even pointless conversations can teach you a thing or two.',
            character: 'Ryou Haruna',
            anime: 'Eden*',
            buttonText: '',

        }
    },

    created() {
        this.$root.$data.favs.forEach(element => {
            if (element == this.id) {
                this.buttonText = "Unfavorite"
            }
        });

        this.buttonText = "Favorite"
    },

    methods: {
        setRandomQuote() {
            console.log("setting random")
            this.random = Math.floor(Math.random() * 10);
            this.id = this.random;
            this.text = this.$root.$data.quotes[this.random].quote;
            this.character = this.$root.$data.quotes[this.random].character;
            this.anime = this.$root.$data.quotes[this.random].anime;
            
            console.log("setting text")
            let isFav = false;

            this.$root.$data.favs.forEach(element => {
                if (element.id == this.id) {
                    
                    this.buttonText = "Unfavorite";
                    isFav = true;
                    return;
                }
            });

            if (!isFav) {
                this.buttonText = "Favorite";
            }
        },

        // isFavorited() {
        //     console.log("in isFav")
        //     this.$root.$data.favs.forEach(element => {
        //         if (element == this.id) {
        //             this.buttonText = "Unfavorite"
        //             return true;
        //         }
        //     });

        //     this.buttonText = "Favorite"
        //     return false;
        // },
    

        toggleFavorite() {

            let isFav = false;

            this.$root.$data.favs.forEach(element => {
                if (element.id == this.id) {
                    console.log("making fav")
                    isFav = true;
                    let itemIndex = this.$root.$data.favs.indexOf(element);

                    this.$root.$data.favs.splice(itemIndex, 1);
                    this.buttonText = "Favorite";
                    return;

                }
            });

            if (!isFav) {
                let addQuote = {id: this.id, anime: this.anime, character: this.character, text: this.text};
            

                console.log("making unfav")
                this.$root.$data.favs.push(addQuote);
                this.buttonText = "Unfavorite";
            }

        }
    },
}
</script>

<style scoped>
.wrapper {
    display: flex;
    flex-direction: row;
    align-items: top;
    justify-content: center;
}

.quote-section {
    min-width: 80%;
}

.buttons {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: top;
    min-width: 20%;
}
</style>
