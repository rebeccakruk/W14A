<template>
    <div>
        <LoudJoke v-if="(joke, index)" :key="index" :joke="joke" @click="loudJoke" />

        <SnakeJoke v-if="joke in jokes" :key="joke" @click="snakeJoke" />
        <button>Random Joke</button>
        {{ jokes }}
    </div>
</template>

<script>
import axios from "axios";
import SnakeJoke from "@/components/SnakeJoke.vue";
import LoudJoke from "@/components/LoudJoke.vue";
// import cookies from "vue-cookies";

export default {
    name: "JokeButton",
    components: {
        SnakeJoke,
        LoudJoke
    },
    data() {
        return {
            jokes: String
        }
    },
    methods: {
        handleJoke(jokes) {
            console.log(jokes);
        }
    },
    mounted() {
        axios.request({
            url: "https://geek-jokes.sameerkumar.website/api?format=json",
            method: "GET"
        }).then((response) => {
            this.jokes = response.data;
        }).catch((error) => {
            console.log(error);
        })
        this.$root.$on(`loudJoke`, this.handleJoke);
        this.$root.$on(`snakeJoke`, this.handleJoke);
    },

}
</script>

<style scoped>

</style>