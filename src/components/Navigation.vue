<template>
    <ul>
        <li><router-link to="/">Home</router-link></li>
        <li><router-link to="/">LONGFORM</router-link></li>
        <li><router-link to="/">GUIDES</router-link></li>
        <li><router-link to="/">SHIELD</router-link></li>
        <li><router-link to="/">PERIPHERALS</router-link></li>
        <li><router-link to="/">DEVICES</router-link></li>
        <li><router-link to="/">DEVELOPERS</router-link></li>
        <li><router-link to="/">GAMES</router-link></li>
        <li><router-link to="/">APPS</router-link></li>
    </ul>
</template>

<script>
    import axios from 'axios';
    import ajax from '../mixins/ajax';

    export default {
        name: "navigation",
        mixins: [ajax],

        data() {
            return {
                menu: []
            }
        },

        created: async function () {
          this.menu = await axios.get('https://api.androidtv.news/wp-json/wp-api-menus/v2/menus/720')
            console.log(this.menu);
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
        background-color: rebeccapurple;
    }
</style>