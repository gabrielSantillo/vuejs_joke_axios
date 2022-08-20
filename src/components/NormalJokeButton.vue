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
    display_joke(normal_joke) {
      /* adding the value received from the emitter to the variable */
      this.joke = normal_joke;
    },
  },

  mounted() {
    /* listen to the custom event that was emmited by JokeButton component, by doing that I'm able to receive the parameter sent by this custom event and called a function that can handle this parameter*/
    this.$root.$on(`normal_joke`, this.display_joke);
  },
};
</script>

<style scoped></style>
