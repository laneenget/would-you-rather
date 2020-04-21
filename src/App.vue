<template>
  <div id="app">

        <h1> Would you rather...</h1>

        <WouldYouRatherQuestionComponent 
            v-for="question in questions" v-bind:key="question.id" v-bind:question="question.question" v-bind:answer1="question.answer1" v-bind:answer2="question.answer2" 
            v-on:answer-changed="answerChanged">
        </WouldYouRatherQuestionComponent>

         {{ userSelectionMessage }}

        <h1> You would rather... </h1>
        <ul>
          <li 
            is="answer-item"
            v-for="(answer, index) in answers"
            v-bind:key="answer.index"
            v-on:remove="answers.splice(index, 1)">{{ answer }}</li>
        </ul>
    </div>
</template>

<script>
import WouldYouRatherQuestionComponent from './components/WouldYouRatherQuestion.vue'

export default {
  name: 'App',
  components: {
    WouldYouRatherQuestionComponent
  },
  data() {
    return {
      questions: [
        {
          id: 0,
          question: 'visit the international space station for a week or stay in an underwater hotel for a week?',
          answer1: 'Visit the international space station',
          answer2: 'Stay in an underwater hotel'
        },
        {
          id: 1,
          question: 'be able to control fire or water?',
          answer1: 'Control fire',
          answer2: 'Control water'
        },
        {
          id: 2,
          question: 'learn to surf or learn to ride a skateboard?',
          answer1: 'Learn to surf',
          answer2: 'Learn to skateboard'
        }
      ],
      userSelectionMessage: '',
      answers: [],
    }
  },
  methods: {
    answerChanged(answer){
      console.log('Event emitted from child.')
      this.userSelectionMessage = `Thanks! You selected ${answer}`
    },
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
