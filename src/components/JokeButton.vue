<template>
    <div class="button_container">
        <button @click="display_normal_joke">Normal Joke</button>
        <button @click="display_snake_joke">Snake Joke</button>
        <button @click="display_loud_joke">Loud Joke</button>
    </div>
</template>

<script>
import axios from "axios";
    export default {
        methods: {
            display_normal_joke() {
                this.$root.$emit(`normal_joke`, this.random_joke)
            },
            display_snake_joke() {
                this.$root.$emit(`snake_joke`, this.random_joke)
            },
            display_loud_joke() {
                this.$root.$emit(`loud_joke`, this.random_joke)
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

<style scoped>
.button_container {
    display: grid;
    grid-auto-flow: column;
    width: 80%;
    place-items: center;
}

</style>