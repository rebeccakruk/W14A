<template>
    <div>
        <button @click="loudJoke">Loud Joke</button>
        <h2>{{ loudFunny }}</h2>

    </div>
</template>

<script>
export default {
    name: "LoudJoke",
    props: {
        loudFunny: String,
    },
    methods: {
        loudJoke() {
            let doesInclude = this.joke.includes(`loud`);
            if (doesInclude === true) {
                this.$root.$emit(`loudJoke`, this.loudJoke);
            }
        }
    }
}

</script>

<style scoped>

</style>