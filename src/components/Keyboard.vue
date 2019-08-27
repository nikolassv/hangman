<template>
    <ul>
        <li 
                v-for="letter in availableLetters" 
                :key="letter"
                v-bind:class="{isSelected: isSelected(letter), isInWord: isInWord(letter)}"
                v-on:click="$emit('click-letter', letter)"
        >{{letter}}</li>
    </ul>
</template>

<script>
    export default {
        name: "Keyboard",
        props: {
            letters: Array,
            availableLetters: Array,
            word: String
        },
        methods: {
            isSelected: function (letter) {
                return this.letters.includes(letter);
            },
            isInWord: function (letter) {
                return this.word.toUpperCase().indexOf(letter) !== -1;
            }
        }
    }
</script>

<style scoped>
    ul {
        display: block;
        margin: 10px auto;
        max-width: 500px;
        width: 80%;
        text-align: center;
    }
    
    li {
        list-style-type: none;
        display: inline-block;
        padding: 8px;
        border: 1px solid #666;
        border-radius: 4px;
        margin-right: 4px;
        margin-bottom: 4px;
        cursor: pointer;
    }
    
    li.isSelected {
        background-color: #ff8f7f;
    }
    
    li.isSelected.isInWord {
        background-color: #aaff93
    }
</style>