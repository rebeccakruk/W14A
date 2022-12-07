<template>
    <div>
        <button @click="snakeJokes">Snake Joke</button>
        {{ snakeFunny }}
    </div>
</template>

<script>
export default {
    name: "SnakeJoke",
    data() {
        return {
            snakeFunny: String,
        }
    },
    methods: {
        snakeJokes() {
            let doesInclude = this.snake.includes(`snake`);
            if (doesInclude === true) {
                this.$root.$emit(`snakeJoke`, this.snakeFunny);
            }
        }
    }
}
</script>

<style scoped>

</style>