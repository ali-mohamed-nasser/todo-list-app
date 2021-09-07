<template>
    <div v-show="showAddTaskPanel" class="AddTaskPanel">
        <form @submit="submitData">
            <Input v-model="text" mainlabel="Task Text" name="task-text" placeholder="Enter your task description" />
            <Input v-model="dateTime" inputType="datetime-local" mainlabel="Task Date & Time" name="task-time" />
            <Input v-model="reminder" inputType="checkbox" :checked="reminder" mainlabel="Set a reminder" name="task-time" />
            <Button className="button-success">Save Task</Button>
        </form>
    </div>
</template>

<script>
import './AddTaskPanel.scss';
import Input from '../Input/Input.vue';
import Button from '../Button/Button.vue';
import dateFormat from 'dateformat';
export default {
    name: 'AddTaskPanel',
    components: {
        Input,
        Button
    },
    methods: {
        submitData(event) {
            event.preventDefault();
            if( !this.text ) {
                alert('You can\'t add a task without text.')
            } else {
                // Convert the date to long date format
                const formatedDate = dateFormat(new Date(this.dateTime), "dddd, mmmm dS, yyyy 'at' h:MM TT");

                // Create a new task to insert
                const newTask = {
                    id: Math.floor(Math.random() * 1000),
                    text: this.text,
                    day: formatedDate,
                    reminder: this.reminder
                }

                // Emit that task to the parent component
                this.$emit('add-task', newTask);

                // Reset the form to default values
                this.text = '';
                this.dateTime = null;
                this.reminder = false;
                this.$emit('hide-add-task-panel');
            }
        }
    },
    props: {
        showAddTaskPanel: Boolean
    },
    data() {
        return {
            text: '',
            dateTime: null,
            reminder: false
        }
    },
    emits: ['add-task']
}
</script>

<style scoped>
    button { margin: 0!important; margin-bottom: 15px!important; float: unset; width: 100%;  }
</style>