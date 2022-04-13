<template>
<div id="app">

    <div id="menu">
        <div id="brand">
            <router-link to="/">
                <img src="/images/logo.png">
            </router-link>
        </div>
        <div id="side">
            <router-link to="/random">
                <div class="menu-item">
                    <p>Random </p>
                </div>
            </router-link>
            <router-link to="/favs">
                <div class="menu-item">
                    <p>{{favSize}} favorites</p>
                </div>
            </router-link>
        </div>
    </div>

    <router-view />
    
    <footer class="footer">
        <h4>Check out my GitHub</h4>
        <a rel="stylesheet" href="insert link here">
            <img src="https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png" alt=""> </a>
    </footer>

</div>
</template>

<script>
export default {
    name: 'App',
    computed: {
        favSize() {
            return this.$root.$data.favs.length;
        }
    }
}
</script>

<style>
* {
    box-sizing: border-box;
}

body {
    margin: 50px 100px;
}

.button {
    display: inline-block;
    padding: 15px 25px;
    margin: 20px;
    font-size: 24px;
    cursor: pointer;
    text-align: center;
    text-decoration: none;
    outline: none;
    color: #fff;
    background-color: #ff7df2;
    border: none;
    border-radius: 15px;
    box-shadow: 0 9px #999;
}

.button:hover {
    background-color: #ffb5f8
}

.button:active {
    background-color: #ff7df2;
    box-shadow: 0 5px #666;
    transform: translateY(4px);
}

#menu {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    grid-column-gap: 5px;
    grid-template-areas: "none brand side";
    margin-bottom: 50px;
    background-color: rgb(255, 225, 253);
}

#menu a {
    color: #B84901;
}

#brand {
    grid-area: brand;
    display: flex;
    justify-content: center;
}

#brand img {
    height: 200px;
}

#side {
    grid-area: side;
    display: flex;
    justify-content: center;
    align-content: center;
}

#side img {
    width: 50px;
}

.menu-item {
    display: flex;
    flex-direction: column;
    padding: 20px;
}

.menu-item p {
    margin: 0px;
}

.browse {
    margin-right: 50px;
}

.footer {
    text-align: center;
    justify-content: center;
    background-color: #fbb6fd;
    padding: 5px;
}

.footer img {
    max-height: 50px;
    margin: 20px auto 20px auto;
}
</style>
