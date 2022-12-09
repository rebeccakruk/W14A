<template>
    <div>
        <button @click="getJoke">Normal Joke</button>
        <h2>{{ normalJoke }}</h2>
    </div>
</template>

<script>
import cookies from 'vue-cookies';
export default {
    name: "JokeButton",
    props: {
        normalJoke: String,
    },
    methods: {
        getJoke() {
            console.log(this.normalJoke);
            this.$root.$emit(`generateJoke`, this.normalJoke);
            cookies.set(`normaljoke`, this.normalJoke);

        }
    },
    mounted() {
        let plainJoke = cookies.get(`normalJoke`);
        console.log(plainJoke);
        this.$root.$emit(plainJoke, this.normalJoke)
    }
}


</script>

<style scoped>

</style>