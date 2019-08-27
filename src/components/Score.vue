<template>
    <div
            v-bind:class="{
                alert:numberOfErrors > 5, 
                ok: numberOfErrors <= 5
            }"
    >{{numberOfErrors}} Fehlversuche</div>
</template>

<script>
    export default {
        name: "Score",
        props: {
            letters: Array,
            word: String
        },
        computed: {
            numberOfErrors: function () {
                const ucWord = this.word.toUpperCase();
                return this.letters.reduce(function (acc, letter) {
                    return acc + ((ucWord.indexOf(letter) === -1) ? 1 : 0);
                }, 0)
            }
        }
    }
</script>

<style scoped>
    div {
        font-size: 1.2em;
        font-weight: bold;
        text-align: center;
    }

    .ok {
        color: #24a454;
    }
    .alert {
        color: #ff2e49;
    }
</style>