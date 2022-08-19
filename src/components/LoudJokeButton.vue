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
    display_joke(loud_joke) {
      let string_loud = loud_joke.toUpperCase();
      this.jokes.push(string_loud);
    },
  },

  mounted() {
    this.$root.$on(`loud_joke`, this.display_joke);
  },
};
</script>

<style scoped></style>
