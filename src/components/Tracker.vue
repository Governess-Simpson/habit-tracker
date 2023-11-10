<template>
    <div class="container">
        <div v-for="month in months">
            <div v-for="day in month.days">
                <component is="div" class="container" :id="makeID">{{ id }}</component>
                <div>{{ id }}</div>
<!--                 <div>
                    {{ month.id }} {{ day }}
                </div> -->
            </div>
        </div>
    </div>
</template>

<script>


export default {
    name: "Tracker",
    props: {
        months: Array,
        timestamp: String
    },
    methods: {
        makeID() {
            console.log(this.month, this.day)
            return this.month + this.day 
        }
    }

}
</script>


<style scoped>
.container {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(5px, 1fr));
    gap: .5em;
    padding: 1em;
}

</style>
<!--   <component is="div">This is a DIV element</component>
 -->
