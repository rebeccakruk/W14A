<template>
    <div>
        <button @click="loudJoke">LOUD JOKE</button>
        <h2>{{ loudFunny.toUpperCase() }}</h2>
    </div>
</template>

<script>
export default {
    name: "LoudJoke",
    props: {
        loudFunny: String,
    },
    data() {
        return {
            loudJokes: Boolean,
        }
    },
    methods: {
        loudJoke() {
            console.log(this.loudFunny);
            console.log(this.loudJokes);
        }
    },
    mounted() {
        this.$root.$emit(`makeCaps`, this.loudFunny);
    },
}


</script>

<style scoped>

</style>