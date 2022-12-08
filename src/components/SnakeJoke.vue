<template>
    <div>
        <!-- <button @click.once="snakeJokes">Snake_Joke</button> -->
        <h2>{{ snakeFunny.replaceAll(' ', '_') }}</h2>

    </div>
</template>

<script>
export default {
    name: "SnakeJoke",
    props: {
        snakeFunny: String,
    },
    data() {
        return {
            displaySnakeJoke: Boolean,
        }
    },
    methods: {
        snakeJokes() {
            if (this.displaySnakeJoke === true) {
                this.snakeFunny.replaceAll(' ', '_');
                console.log(this.snakeFunny);
            }
            this.$emit(`snakeJokes`, this.snakeFunny);
            this.$emit(`snakeJokes`, this.displaySnakeJoke);
        }
    },
}




</script>

<style scoped>

</style>