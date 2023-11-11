<template>
  <!-- Passes in the data values into Form.vue, alongside listening for when a new radio button is pressed. -->
  <Form :question="question" :answers="answers" @update="updatedSelectedAnswer" />
  <Tracker :months="months" :currentDate="currentDate" :currentMonth="currentMonthName" :opacity="opacity"/>
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
      currentDate: 0,
      currentMonth: '',
      opacity: 0,
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
          ],
      /* Varying opacity levels of the cells depending on the option the user selected. */
      opacityLevel: [
            {
              id: "I put my gym clothes on.",
              opacity: .1
            },
            {
              id: "I went inside the gym.",
              opacity: .2
            },
            {
              id: "I performed light activity (cardio/stretch, < 30 minutes).",
              opacity: .33
            },
            {
              id: "I performed heavy cardio (> 30 minutes).",
              opacity: .5
            },
            {
              id: "I lifted weights.",
              opacity: .75
            },
            {
              id: "I performed cardio AND weights.",
              opacity: 1
            }
          ]
        }
      },
  created() {
      setInterval(this.getNow, 1000);
    },
  /* 
  When a new radio button is pressed, that value is updated to "selectedAnswer". The opacity of the cell is also determined based on the selectedAnswer.
  */
  methods: {
    updatedSelectedAnswer(newAnswer){
      this.selectedAnswer = newAnswer;
      this.opacityLevel.forEach(entry => {
                entry.id === this.selectedAnswer ? this.opacity = entry.opacity : console.log() 
            })
    },
    getNow() {
          const today = new Date();
          const currentMonth = today.getMonth()+1
          const currentDate = today.getDate()
          this.currentDate = currentDate
          this.currentMonth = currentMonth
        }
  },
  computed: {
    currentMonthName() {
      switch(this.currentMonth){
        case 1:
          return "January"
        case 2:
          return "February"
        case 3:
          return "March"
        case 4:
          return "April"
        case 5:
          return "May"
        case 6:
          return "June"
        case 7:
          return "July"
        case 8:
          return "August"
        case 9:
          return "September"
        case 10:
          return "October"
        case 11:
          return "November"
        case 12:
          return "December"
        default:
          break
      }
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
