<template>
    <div>
        
        <h2>{{ question }}</h2>

        <input type="radio" v-model="choice" v-bind:value="answer1" v-on:change="$emit('answer-changed', choice)">
        <label>{{ answer1 }}</label>
        <input type="radio" v-model="choice" v-bind:value="answer2" v-on:change="$emit('answer-changed', choice)">
        <label>{{ answer2 }}</label>

    </div>
</template>

<script>

export default {
    name: 'WouldYouRatherQuestionComponent',
    data() {
        return{
            choice: ''
        }
    },
    props: {
        question: String,
        answer1: String,
        answer2: String
    }
}
</script>