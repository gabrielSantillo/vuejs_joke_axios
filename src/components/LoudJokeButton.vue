<template>
  <div v-if="joke !== undefined">
    <h4>{{ joke }}</h4>
  </div>
</template>

<script>
export default {
  data() {
    return {
      /* variable initialized as undefined */
      joke: undefined,
    };
  },

  methods: {
    /* this function is called after the listener receive the parameter from the emitter */
    display_joke(loud_joke) {
      /* this line of code receives the parameter and change all letters to Upper Case letters*/
      let string_loud = loud_joke.toUpperCase();
      /* adding the value received from the emitter to the variable */
      this.joke = string_loud;
    },
  },

  mounted() {
    /* listen to the custom event that was emmited by JokeButton component, by doing that I'm able to receive the parameter sent by this custom event and called a function that can handle this parameter*/
    this.$root.$on(`loud_joke`, this.display_joke);
  },
};
</script>

<style scoped></style>
