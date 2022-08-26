<template>
    <div style="display:flex;height:100%;gap:15px">
        <div id="sched-bar">
            <h1>Add Schedule Here</h1>
            <form @submit="addClass" class="add-form">
                Class Name <input v-model="classname" placeholder="Kas 1" name="classname"/> <br/>
                Time
                <input v-model="timestart" placeholder="07:30AM" name="timestart" style="width:5rem"/> -
                <input v-model="timeend" placeholder="07:30PM" name="timeend" style="width:5rem"/> <br/>
                Day 
                <select v-model="classday">
                    <option value="0">Sunday</option>
                    <option value="1">Monday</option>
                    <option value="2">Tuesday</option>
                    <option value="3">Wednesday</option>
                    <option value="4">Thursday</option>
                    <option value="5">Friday</option>
                    <option value="6">Saturday</option>
                </select> <br/>
                <input type="submit"/>
            </form>
            <br/>
            <ClassSchedule/>
        </div>
        <div>
            Schedule Shows Here
            
            <div v-for="c in classes" :key="c.classname">
                {{c.classname}}
            </div>

        </div>
    </div>
</template>

<script>
import ClassSchedule from './components/ClassSchedule.vue'

export default {
    data() {
        return {
            classes: []
        }
    },
    components: {
        ClassSchedule
    },
    methods: {
        addClass(e) {
            e.preventDefault()

            console.log(this.classes)

            let schedule = {
                classname: this.classname,
                timestart: this.timestart,
                timeend: this.timeend,
                day: this.classday
            }

            this.classes.push(schedule)
        }
    }
}

</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
}

#sched-bar {
    width: 25%;
    height: 100;
    border-right: 1px solid gray;
}

</style>
