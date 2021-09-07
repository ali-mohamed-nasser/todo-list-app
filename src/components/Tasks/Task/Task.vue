<template>
    <div @dblclick="$emit('toggle-reminder', task.id)" :class="[task.reminder ? 'Reminder' :'', 'Task']">
        <h4>{{ task.text }}</h4>
        <p>{{ task.date }}</p>
        <i class="fas fa-light fa-trash" @click="$emit('delete-task', task.id)"></i>
    </div>
</template>

<script>
import './Task.scss';

export default {
    name: 'Task',
    props: {
        task: Object
    },
    emits:['delete-task', 'toggle-reminder']
}
</script>
