<template>
  <div id="app">
    <SnakeJoke :class="snakeJokes" v-for="snake in jokes" :key="snake" :snakeFunny="snake" />
    <JokeButton v-for="(normal, index) in jokes" :key="index" :normalJoke="normal" />
    <LoudJoke v-for="(loud, capJoke) in jokes" :key="capJoke" :loudFunny="loud" />
    <button @click="newJoke()">New Joke</button>
  </div>
</template>
@styleSnake="callback"

<script>
import axios from "axios";
import SnakeJoke from "@/components/SnakeJoke.vue";
import LoudJoke from "@/components/LoudJoke.vue";
import JokeButton from "@/components/JokeButton.vue";


export default {
  name: "App",
  components: {
    SnakeJoke,
    LoudJoke,
    JokeButton,
  },
  data() {
    return {
      jokes: [],
    }
  },
  methods: {
    snakeJokes() {
      this.displaySnakeJoke = !this.displaySnakeJoke;
      console.log(this.displaySnakeJoke);
    },
    newJoke() {
      axios.request({
        url: "https://geek-jokes.sameerkumar.website/api?format=json",
        method: "GET",
      })
        .then((response) => {
          this.jokes = response.data;
          console.log(this.jokes);
        })
        .catch((error) => {
          console.log(error);
        }),
        this.$root.$on(`styleSnake`, this.snakeFunny);
      this.$root.$on(`plainJoke`, this.normalJoke)
    }
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
