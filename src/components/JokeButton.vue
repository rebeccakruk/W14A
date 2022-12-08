<template>
    <div>
        <button @click="getJoke">Normal Joke</button>
        <h2>{{ normalJoke }}</h2>
    </div>
</template>

<script>

export default {
    name: "JokeButton",
    props: {
        normalJoke: String,
    },
    data() {
        return {
            displayNormalJoke: Boolean,
        }
    },
    methods: {
        getJoke() {
            console.log(this.normalJoke);
        }
    },
    mounted() {
        this.$root.$emit(`generateJoke`, this.normalJoke);
    }
}

</script>

<style scoped>

</style>