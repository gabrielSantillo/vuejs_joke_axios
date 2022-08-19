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
    /* this function is called after the user click in the normal joke button */
    display_normal_joke() {
      /* emitting the custom event so other componets can listen to it, in this case the custom event is named as normal_joke and the parameter past is the joke from the API*/
      this.$root.$emit(`normal_joke`, this.random_joke);
    },
    /* this function is called after the user click in the normal joke button */
    display_snake_joke() {
      /* emitting the custom event so other componets can listen to it, in this case the custom event is named as snake_joke and the parameter past is the joke from the API*/
      this.$root.$emit(`snake_joke`, this.random_joke);
    },
    /* this function is called after the user click in the normal joke button */
    display_loud_joke() {
      /* emitting the custom event so other componets can listen to it, in this case the custom event is named as loud_joke and the parameter past is the joke from the API*/
      this.$root.$emit(`loud_joke`, this.random_joke);
    },
  },
  data() {
    return {
      /* setting this variable to undefined */
      random_joke: undefined,
    };
  },

  /* when the page loads, a axios request is made */
  mounted() {
    axios
      .request({
        url: `https://ron-swanson-quotes.herokuapp.com/v2/quotes`,
      })
      /* if has success in the requesting process call the this arrow function */
      .then((response) => {
        /* giving the value the value of the response form the API to this variable */
        this.random_joke = response[`data`][0];
      })
      /* if fails call this function */
      .catch((error) => {
        console.log(error);
      });
  },
};
</script>

<style scoped>
.button_container {
  display: grid;
  grid-auto-flow: column;
  width: 80%;
  place-items: center;
}
</style>
