<template>
<div>
    <div class="wrapper">

        <h1>Looking for quotes? We've got you.</h1>

        <p>We've got all the best quotes from the most popular shows.</p>
        <p>Save your favorites and view them later--</p>
        <p>Click the button below to go to our advanced quote generator!</p>

        <router-link to="/random">
          <button class="button">Let's Go</button>
        </router-link>

        <div class="gallery">
            <div class="picture col-md col-lg">
                <img src="https://images.unsplash.com/photo-1522383225653-ed111181a951?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxzZWFyY2h8MjY0fHxhbmltZXxlbnwwfHwwfHw%3D&auto=format&fit=crop&w=400&q=60" class="img-fluid">
            </div>
            <div class="picutre col-md col-lg">
                <img src="https://images.unsplash.com/photo-1625895197185-efcec01cffe0?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxzZWFyY2h8NDN8fGFuaW1lfGVufDB8fDB8fA%3D%3D&auto=format&fit=crop&w=400&q=60" class="img-fluid">
            </div>
            <div class="picture col-md col-lg">
                <img src="https://images.unsplash.com/photo-1502246170363-97cb63f36c81?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxzZWFyY2h8MjQwfHxhbmltZXxlbnwwfHwwfHw%3D&auto=format&fit=crop&w=400&q=60" class="img-fluid">
            </div>
        </div>

    </div>
    <!-- <RandomForm :products="products" /> -->
</div>
</template>

<script>
// import ProductList from "../components/ProductList.vue"
export default {
    name: 'HomeView',
    // components: {
    //     ProductList
    // },
    data() {
        return {
            searchText: '',
        }
    },
    computed: {
        products() {
            return this.$root.$data.products.filter(product => product.name.toLowerCase().search(this.searchText.toLowerCase()) >= 0);
        }
    },
}
</script>

<style scoped>
.wrapper {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}

.gallery {
    display: flex;
    flex-direction: row;
    padding: 20px;
}


.picture {
    width: 30%;
}

.search {
    border: 1px solid #ccc;
    border-radius: 4px;
    width: 50%;
}

form {
    display: table;
    width: 100%;
}

i {
    display: table-cell;
    padding-left: 10px;
    width: 1px;
}

input {
    display: table-cell;
    font-size: 20px;
    border: none !important;
    box-shadow: none !important;
    width: 100%;
    height: 40px;
}

.photo img {
    width: 30%;
    max-height: 500px;
}
</style>
