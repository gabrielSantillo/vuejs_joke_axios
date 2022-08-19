<template>
  <div v-if="jokes.length > 0">
    <div v-for="(joke, index) in jokes" :key="index">
      <h4>{{ joke }}</h4>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      /* array initialized to receive the jokes as strings */
      jokes: [],
    };
  },

  methods: {
    /* this function is called after the listener receive the parameter from the emitter */
    display_joke(normal_joke) {
      /* adding the joke into the array */
      this.jokes.push(normal_joke);
    },
  },

  mounted() {
    /* listen to the custom event that was emmited by JokeButton component, by doing that I'm able to receive the parameter sent by this custom event and called a function that can handle this parameter*/
    this.$root.$on(`normal_joke`, this.display_joke);
  },
};
</script>

<style scoped></style>
