<template>
  <div id="app">
    <button @click.once="normalJoke">Normal Joke</button>
    <button @click.once="loudJokes">LOUD JOKES</button>
    <button @click.once="snakeJokes">Snake_Joke</button>
    <!-- <button @click="newJoke">New Joke</button> -->
    <SnakeJoke :class="snake" v-for="(snake, i) in jokes" :key="i" :snakeFunny="snake" />
    <JokeButton v-for="(normal, index) in jokes" :key="index" :normalJoke="normal" />
    <LoudJoke v-for="(loud, capJoke) in jokes" :key="capJoke" :loudFunny="loud" />
  </div>
</template>

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
      isDisplaySnakeJoke: true,
    }
  },
  methods: {
    normalJoke() {
      this.displayNormalJoke = !this.displayNormalJoke;
    },
    snakeJokes() {
      this.displaySnakeJoke = !this.displayNormalJoke;
    },
    loudJokes() {
      this.displayLoudJoke = !this.displayLoudJoke;
    },
  },
  mounted() {
    axios
      .request({
        url: "https://geek-jokes.sameerkumar.website/api?format=json",
        method: "GET",
      })
      .then((response) => {
        this.jokes = response.data;
        console.log(`where is this coming from`);
      })
      .catch((error) => {
        console.log(error);
      });
    this.$root.$on('generateJoke', this.normalJoke);
    this.$root.$on('makeCaps', this.LoudJoke);
    this.$root.$on(`snakeIt`, this.displaySnakeJoke);
    this.$root.$on(`snakeIt`, this.snakeFunny);
  },
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
