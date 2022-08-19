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
    display_joke(normal_joke) { 
      this.jokes.push(normal_joke);
    },
  },

  mounted() {
    this.$root.$on(`normal_joke`, this.display_joke);
  },
};
</script>

<style scoped></style>
