<template>
    <div v-for="month in months">
        <div v-if="month.id === currentMonth">
            <div class="gridView">
                <div v-for="day in month.days">
                    <div :id="createDivId(month.id, day)"></div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import { tSThisType } from '@babel/types';



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
    margin: -200px 500px;
    border: solid red;
    display: grid;
    width: 200px;
    height: 100px;
    grid-template-columns: repeat(auto-fit, minmax(25px, 1fr));
    font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
/*     gap: .5em;
 */   
/*     padding: 1em;
 */}

</style>
<!--   <component is="div">This is a DIV element</component>
 -->
