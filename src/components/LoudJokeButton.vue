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
      this.jokes.push(loud_joke);
    },
  },

  mounted() {
    this.$root.$on(`loud_joke`, this.display_joke);
  },
};
</script>

<style scoped></style>