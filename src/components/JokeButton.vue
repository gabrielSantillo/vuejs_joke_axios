<template>
  <div>
    <button @click="generate_joke">Generate a Joke</button>
    <hr />
    <div v-if="is_joke_generated === true">
      <h3>Click a button a chose the way you want to see the joke</h3>
    </div>
    <div class="button_container">
      <button @click="display_normal_joke">Normal Joke</button>
      <button @click="display_snake_joke">Snake Joke</button>
      <button @click="display_loud_joke">Loud Joke</button>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  methods: {
    /* This function is called after the user clicks in the button that generate the joke  */
    generate_joke() {
      /* changing the value of the variable to true */
      this.is_joke_generated = true;
      /* Making the API request */
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
      is_joke_generated: false,
    };
  },

  /* when the page loads, a axios request is made */
};
</script>

<style scoped>
.button_container {
  display: grid;
  grid-auto-flow: column;
  place-items: center;
  margin-top: 50px;
}
</style>
