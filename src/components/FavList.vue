<template>
<div class="wrapper">
    <ul class="items">
        <li class="item" v-for="item in items" :key="item.id">

            <div class="quote-section">
                <h1 class="quoteText">{{item.text}}</h1>
                <p class="characterName"><em>--{{item.character}}</em> </p>
                <h3 class="animeName">{{item.anime}}</h3>
            </div>

            <button @click="removeItem(item)" class="auto">Remove</button>

        </li>
    </ul>
</div>
</template>

<script>
export default {
    name: 'FavList',
    props: {
        items: Array
    },
    methods: {
        removeItem: function (item) {
            let itemIndex = this.$root.$data.favs.indexOf(item);

            this.$root.$data.favs.splice(itemIndex, 1);
        }
    }
}
</script>

<style scoped>
.wrapper {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
}

.info {
    background: #F2921D;
    color: #000;
    padding: 10px 30px;
    height: 80px;
}

.info h1 {
    font-size: 16px;
}

.info h2 {
    font-size: 14px;
}

.info p {
    margin: 0px;
    font-size: 10px;
}

.price {
    display: flex;
}

button {
    height: 50px;
    background: #000;
    color: white;
    border: none;
    margin-top: 10px;
}

.auto {
    margin-left: auto;
}
</style>
