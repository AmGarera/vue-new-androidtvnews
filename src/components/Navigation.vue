<template>
    <nav class="navbar" role="navigation" aria-label="main navigation">
        <div class="navbar-brand">
            <a class="navbar-item" href="/">
                <img src="https://api.androidtv.news/wp-content/uploads/2016/05/androidtvnewstWHITEfixed.png" alt="Android TV News">
            </a>
        </div>
        <div class="navbar-menu">
    <ul>
        <li v-for=" item in menu.data">
            <!--Make Router-link dynamic, this needs to be solved somehow-->
            <router-link :to="{ name: 'page', params: { page: item.page } }">
                {{ item.title }}
            </router-link>
        </li>
    </ul>
        </div>
    </nav>
</template>

<script>
    import axios from 'axios';
    import ajax from '../mixins/ajax';

    export default {
        name: "navigation",
        mixins: [ajax],

        data() {
            return {
                item: [],
                menu: {
                    title: []
                }
            }
        },

        created: async function () {
            this.menu = await axios.get('https://api.androidtv.news/wp-json/wp-api-menus/v2/menu-locations/primary');
            console.log(this.menu.data[0].title);

        }
    }

</script>

<style scoped>
    ul {
        list-style-type: none;
        margin: 0;
        padding: 0;
        overflow: hidden;
        background-color: grey;
    }

    li {
        float: left;
        font-family: 'Nunito', sans-serif;
    }

    li a {
        display: block;
        color: white;
        text-align: center;
        padding: 14px 16px;
        text-decoration: none;
    }

    /* Change the link color to #111 (black) on hover */
    li a:hover {
        background-color: teal;
    }
    .navbar {
        background-color: grey;
    }
</style>