<template>
  <!-- Passes in the data values into Form.vue, alongside listening for when a new radio button is pressed. -->
  <Form :question="question" :answers="answers" @update="updatedSelectedAnswer" />
  <Tracker :months="months" :timestamp="timestamp"/>
</template>

<script>
import Form from './components/Form.vue'
import Tracker from './components/Tracker.vue'

export default {
  name: 'App',
  components: {
    Form,
    Tracker
  },
  data() {
    return {
      question: "What did you accomplish today?",
      answers: ["I put my gym clothes on.", "I went inside the gym.", "I performed light activity (cardio/stretch, < 30 minutes).", "I performed heavy cardio (> 30 minutes).", "I lifted weights.", "I performed cardio AND weights."],
      selectedAnswer: '',
      timestamp: '',
      months: [
            {
              id: "January",
              days: 31
            },
            {
              id: "February",
              days: 28
            },
            {
              id: "March",
              days: 31
            },
            {
              id: "April",
              days: 30
            },
            {
              id: "May",
              days: 31
            },
            {
              id: "June",
              days: 30
            },
            {
              id: "July",
              days: 31
            },
            {
              id: "August",
              days: 31
            },
            {
              id: "September",
              days: 30
            },
            {
              id: "October",
              days: 31
            },
            {
              id: "November",
              days: 30
            },
            {
              id: "December",
              days: 31
            }
          ]
        }
      },
  created() {
      setInterval(this.getNow, 1000);
    },
  /* 
  When a new radio button is pressed, that value is updated to "selectedAnswer".
  */
  methods: {
    updatedSelectedAnswer(newAnswer){
      this.selectedAnswer = newAnswer
    },
    getNow() {
          const today = new Date();
          const time = (today.getMonth()+1) + '-' + today.getDate()
          this.timestamp = time
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
