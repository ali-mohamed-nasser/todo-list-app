<template>
    <div :class="[task.reminder ? 'Reminder' :'', 'Task']">
        <h4>{{ task.text }}</h4>
        <p>{{ task.day }}</p>
        <i class="fas fa-times" @click="deleteTask(task.id)"></i>
    </div>
</template>

<script>
import './Task.scss';

export default {
    name: 'Task',
    props: {
        task: Object
    },
    methods: {
        deleteTask(taskID) {
            console.log('delete task ' + taskID);
        }
    }
}
</script>
