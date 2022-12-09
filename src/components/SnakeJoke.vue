<template>
    <div>
        <button @click="$emit(`styleSnake`)">Snake_Joke</button>
        <h2 v-if="(isSnake = true)">{{ snakeFunny.replaceAll(' ', '_') }}</h2>
    </div>
</template>

<script>
import cookies from 'vue-cookies';
export default {
    name: "SnakeJoke",
    props: {
        snakeFunny: String,
    },
    data() {
        return {
            isSnake: false,
        }
    },
    methods: {
        isSnakeOn() {
            this.isSnake = !this.isSnake;
            console.log(this.isSnake);
        },
        emitSnakeFunny() {
            this.$root.$emit(`snakeFunny`, this.snakeFunny)
            cookies.set('styleSnake', "Snake_Joke");
        },
        styleSnake() {
            let styleSnake = cookies.get(`styleSnake`);
            if (styleSnake == 'Snake_Joke') {
                'Snake_Joke'.replaceAll(' ', '_');
            }
        }
    },
    mounted() {
        let styleSnake = cookies.get(`styleSnake`);
        if (styleSnake == 'Snake_Joke') {
            this.$root.$emit(`styleSnake`, this.snakeFunny);
        }
    },
}




</script>

<style scoped>

</style>