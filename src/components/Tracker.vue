<template>
    <!-- Iterate through all months, and only display the month/days that we are currently in. -->
    <div v-for="month in months">
        <div v-if="month.id === currentMonth">
            <div class="gridView">
                <div v-for="day in month.days">
                    <!-- If an opacity value has been defined at least once (aka, someone has made a submission), update the background color and opacity accordingly. Space is to maintain the grid-like appearance. -->
                    <KeepAlive>
                        <div :id="createDivId(month.id, day)" class="noColor" v-bind:style="[ isOpacity && day === currentDate ? {'background-color': 'red', 'opacity': this.opacity} : '']">&nbsp;</div>
                    </KeepAlive>
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
        currentMonth: String,
        opacity: Number
    },
    data() {
        return {
            id: 1,
            /* Automatically set to false when no button is pressed; will always remain true after the first selection. */
            isOpacity: false
        }
    },
    /* Creates a unique Div ID for each cell that can be referenced later. */
    methods: {
        createDivId(month, day) {
                this.id = month + day
       }
    },
    /* Watching for whenever the opacity value changes (aka, when the submit button is clicked), and adjusting the isOpacity varaible. Probably can refactor since it's redundant after the first click. */
    watch: {
        opacity(newVal, oldVal){
            this.isOpacity = true
        }
    }
}
</script>


<style scoped>

.gridView {
    margin: -550px 875px;
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
