<template>
    <div v-for="month in months">
        <div v-if="month.id === currentMonth">
            <div class="gridView">
                <div v-for="day in month.days">
                    <div :id="createDivId(month.id, day)" class="noColor">{{ day }}</div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>


export default {
    name: "Tracker",
    props: {
        months: Array,
        currentDate: Number,
        currentMonth: String
    },
    data() {
        return {
            id: 1
        }
    },
    methods: {
        createDivId(month, day) {
                this.id = month + day
            }
        }
}
</script>


<style scoped>

.gridView {
    margin: -600px 850px;
    display: grid;
    width: 500px;
    height: 500px;
    grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
    font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
}

.noColor {
    display: flex;
    border: 1px solid black;
    height: 85px;
    width: 100px;
    justify-content: center;
}

</style>
<!--   <component is="div">This is a DIV element</component>
 -->
