<template>
  <!-- Passes in the data values into Form.vue, alongside listening for when a new radio button is pressed. -->
  <Form :question="question" :answers="answers" @update="updatedSelectedAnswer"/>
  <div>
    {{ selectedAnswer }}
  </div>
</template>

<script>
import Form from './components/Form.vue'

export default {
  name: 'App',
  components: {
    Form
  },
  data() {
    return {
      question: "What did you accomplish today?",
      answers: ["I put my gym clothes on.", "I went inside the gym.", "I performed light activity (cardio/stretch, < 30 minutes).", "I performed heavy cardio (> 30 minutes).", "I lifted weights.", "I performed cardio AND weights."],
      selectedAnswer: '',
    }
  },
  /* 
  When a new radio button is pressed, that value is updated to "selectedAnswer".
  */
  methods: {
    updatedSelectedAnswer(newAnswer){
      this.selectedAnswer = newAnswer
    }
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
