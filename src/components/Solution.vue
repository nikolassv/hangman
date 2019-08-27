<template>
    <ul>
        <li
            v-for="letter in solutionLetters"
            :key="letter.index"
            v-bind:class="{toBeGuessed: !letter.isCorrect}"
        >
            <span v-if="letter.isCorrect">{{letter.letter}}</span>
            <span v-else>&nbsp;</span>
        </li>
    </ul>
</template>

<script>
    export default {
        name: "Solution",
        props: {
            word: String,
            knownLetters: Array,
            availableLetters: Array
        },
        computed: {
            solutionLetters: function solutionLetters() {
                let solutionLetters = [];
                let ucWord = this.word.toUpperCase();
                for (let i = 0; i < ucWord.length; i++) {
                    let isCorrect = !this.availableLetters.includes(ucWord[i]) || this.knownLetters.includes(ucWord[i])
                    solutionLetters.push({index: i, letter: ucWord[i], isCorrect: isCorrect});
                }
            return solutionLetters;

            }
        }
    }
</script>

<style scoped>
    ul {
        margin: 20px auto;
        text-align: center;
    }
    
    li {
        list-style-type: none;
        width: 22px;
        margin-right: 2px;
        font-size: 2em;
        display: inline-block;
        text-align: center;
    }
    
    li.toBeGuessed {
        border-bottom: 2px solid #7d8fff;
    }
</style>