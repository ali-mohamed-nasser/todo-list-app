<template>
    <div class="AddTaskPanel">
        <form @submit="logData">
            <Input v-model="text" mainlabel="Task Text" name="task-text" placeholder="Enter your task description" />
            <Input v-model="dateTime" inputType="datetime-local" mainlabel="Task Date & Time" name="task-time" />
            <Input v-model="reminder" inputType="checkbox" mainlabel="Set a reminder" name="task-time" />
            <Button className="button-success">Save Task</Button>
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
        logData(event) {
            event.preventDefault();
            console.log("the text is: " + this.text, "the time is: " + this.dateTime, "the reminder is: " + this.reminder);
        }
    },
    data() {
        return {
            text: '',
            dateTime: null,
            reminder: false
        }
    }
}
</script>

<style scoped>
    button { margin: 0!important; margin-bottom: 15px!important; float: unset; width: 100%;  }
</style>