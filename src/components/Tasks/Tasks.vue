<template>
    <div class="Tasks" :key="task.id" v-for="task in tasks">
        <Task :task="task" />
    </div>
</template>

<script>
import './Tasks.scss';
import Task from './Task/Task.vue';
export default {
    name:'Tasks',
    props: {
        tasks: Array
    },
    components: {
        Task
    }
}
</script>
