<template>
    <div>
        <button @click="display_joke">Normal Joke</button>
    </div>
</template>

<script>
import axios from "axios";
    export default {
        methods: {
            display_joke() {
                this.$root.$emit(`random_joke`, this.random_joke)
            }
        },
        data() {
            return {
                random_joke: undefined
            }
        },

        mounted () {
            axios.request({
                url: `https://ron-swanson-quotes.herokuapp.com/v2/quotes`
            }).then((response) => {
                 this.random_joke = response[`data`][0];
            }).catch((error) => {
                console.log(error);
            });
        },
    }
</script>

<style lang="scss" scoped>

</style>