<template>
    <div>{{ question }}</div>
    <!-- :key="index" is for performance-related concerns in Vue, could omit. iterate through all array values -->
    <div v-for="(answer, index) in answers" :key="index">
        <!-- define styling class + creates label/radio button for each array value. -->
        <!-- name makes sure only one radio button can be pressed. id connects to label, value displays array content. -->
        <!-- v-model defines that the value of the radio button can be sent to computed for additional processing. -->
        <label :for="index" class="radio_buttons">{{ answer }}</label>
        <input type="radio" :id="index" :value="answer" name="activityLevel" v-model="selectedAnswer">
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
