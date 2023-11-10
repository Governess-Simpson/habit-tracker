<template>
    <div class="form">
        <h2>{{ question }}</h2>
        <br>
        <!-- :key="index" is for performance-related concerns in Vue, could omit. iterate through all array values -->
        <div v-for="(answer, index) in answers" :key="index">
            <!-- define styling class + creates label/radio button for each array value. -->
            <!-- name makes sure only one radio button can be pressed. id connects to label, value displays array content. -->
            <!-- v-model defines that the value of the radio button can be sent to computed for additional processing. -->
            <input type="radio" :id="index" :value="answer" name="activityLevel" class="radio_buttons" v-model="selectedAnswer">
            <label :for="index" class="radio_labels">{{ answer }}</label>
        </div>
    </div>
</template>


<script>
export default{
    name: "Form",
    /* Define props being sent by App.vue */
    props: {
        question: String,
        answers: Array
    },
    computed: {
        /* Connects to v-model. Defines setter (custom emit function to send value to App.vue) and getter functions. */
        selectedAnswer: {
            get() {
                return this.answer
            },
            set(val) {
                this.$emit('update', val);
            } 
        }
    }
}
</script>


<style scoped>

.form {
    min-height: 200px;
    width: 650px;
    text-align: left;
    padding: 15px;
    margin: 0 100px;
    font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
}

.form h2 {
    font-size: 30px;
    text-transform: capitalize;
}

.form label{
    font-size: 20px;
    text-transform: capitalize;
}


input[type="radio"]+label:hover {
  cursor: pointer;
  border-color: #73daa1;
  color: #73daa1;
}

input[type="radio"]:checked + label {
  border-color: #00AD51;
  color: #00AD51;
}

.radio_buttons {
    margin-bottom: 75px;
    margin-right: 10px;
    width: 20px;
    height: 20px;
}


</style>
