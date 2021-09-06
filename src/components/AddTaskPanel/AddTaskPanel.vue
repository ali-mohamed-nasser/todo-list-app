<template>
    <div class="AddTaskPanel">
        <form action="/">
            <Input v-model="text" @input-change="textChange" mainlabel="Task Text" name="task-text" placeholder="Enter your task description" />
            <Input v-model="dateTime" @input-change="timeChange" inputType="datetime-local" mainlabel="Task Date & Time" name="task-time" />
            <Input v-model="reminder" @input-change="reminderChange" inputType="checkbox" mainlabel="Set a reminder" name="task-time" />
            <Button @click="logData" className="button-success">Save Task</Button>
        </form>
    </div>
</template>

<script>
import './AddTaskPanel.scss';
import Input from '../Input/Input.vue';
import Button from '../Button/Button.vue';
export default {
    name: 'AddTaskPanel',
    components: {
        Input,
        Button
    },
    methods: {
        textChange(inputValue) {
            this.text = inputValue;
        },
        timeChange(inputValue) {
            this.dateTime = inputValue;
        },
        reminderChange(inputValue) {
            this.reminder = inputValue;
        },
        logData(event) {
            event.preventDefault();
            console.log("the text is: " + this.text, "the time is: " + this.dateTime, "the reminder is: " + this.reminder);
        }
    },
    data() {
        return {
            text: '',
            dateTime: null,
            reminder: null
        }
    }
}
</script>

<style scoped>
    button { margin: 0!important; margin-bottom: 15px!important; float: unset; width: 100%;  }
</style>