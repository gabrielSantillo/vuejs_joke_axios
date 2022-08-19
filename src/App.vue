<template>
  <div id="app"> 
    <joke-button></joke-button>
    <normal-joke-button></normal-joke-button>
    <snake-joke-button></snake-joke-button>
    <loud-joke-button></loud-joke-button>
  </div>
</template>

<script>
import JokeButton from './components/JokeButton.vue'
import LoudJokeButton from './components/LoudJokeButton.vue'
import NormalJokeButton from './components/NormalJokeButton.vue'
import SnakeJokeButton from './components/SnakeJokeButton.vue'

export default {
  name: 'App',
  components: {
    NormalJokeButton,
    SnakeJokeButton,
    LoudJokeButton,
    JokeButton
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
