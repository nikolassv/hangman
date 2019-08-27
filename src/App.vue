<template>
    <div>
        <div>
            <h1>Hangman</h1>
            <solution
                    v-bind:word="word"
                    v-bind:known-letters="letters"
                    v-bind:available-letters="availableLetters"
            ></solution>
            <keyboard
                    v-bind:letters="letters"
                    v-bind:available-letters="availableLetters"
                    v-bind:word="word"
                    v-on:click-letter="addLetter($event)"
            ></keyboard>
            <button
                    v-on:click="reset()"
            >Neustarten</button>
            <score
                    v-bind:word="word"
                    v-bind:letters="letters"
            ></score>
        </div>
        <footer>By <a href="http://nikolassv.de" target="_blank">Nikolas Schmidt-Voigt</a></footer>
    </div>
</template>

<script>
    import Solution from './components/Solution.vue';
    import Keyboard from './components/Keyboard.vue';
    import Score from './components/Score.vue';
    import words from './assets/wordLibrary.js';

    export default {
        name: 'app',
        components: {
            Solution,
            Keyboard,
            Score
        },
        data: function () {
            return {
                word: words[Math.floor(Math.random() * words.length)],
                letters: [],
                availableLetters: ['A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K', 'L', 'M', 'N', 'O', 'P', 'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z', 'Ä', 'Ö', 'Ü']
            };
        },
        methods: {
            addLetter: function (letter) {
                if (!this.letters.includes(letter)) {
                    this.letters.push(letter);
                }
            },
            reset: function () {
                this.letters = [];
                this.word = words[Math.floor(Math.random() * words.length)];
            }
        }
    }
</script>

<style>
    div {
        font-family: "Helvetica Neue", Helvetica, sans-serif;
        text-align: center;
    }
    
    button {
        margin: 20px 0;
        font-size: 1.1em;
        color: #333;
        background-color: unset;
        border: 2px solid #7d8fff;
        border-radius: 6px;
        padding: 3px 25px;
    }

    footer {
        margin-top: 3em;
        font-size: 70%;
    }
</style>
