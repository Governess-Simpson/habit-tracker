<template>
    <div>{{ question }}</div>
    <div v-for="(answer, index) in answers" :key="index">
        <label :for="index" class="radio_buttons">{{ answer }}</label>
        <input type="radio" :id="index" :value="answer" name="activityLevel" v-model="selectedAnswer">
    </div>
</template>


<script>
export default{
    name: "Form",
    props: {
        question: String,
        answers: Array
    },
    computed: {
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
