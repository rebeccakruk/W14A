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
    methods: {
        loudJoke() {
            this.$root.$emit(`makeCaps`, this.loudFunny);
        }
    }
}


</script>

<style scoped>

</style>