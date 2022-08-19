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
      jokes: [],
    };
  },

  methods: {
    display_joke(snake_joke) {
      let string_snake = snake_joke.replace(/ /g, `_`);
      this.jokes.push(string_snake);
    },
  },

  mounted() {
    this.$root.$on(`snake_joke`, this.display_joke);
  },
};
</script>

<style scoped></style>
