<template>
    <div class="Header">
        <div class="title"><h3>{{ title }}</h3></div>
        <Button @button-clicked="$emit('button-clicked')" :className="showAddTaskPanel ? 'button-danger' : 'button-success'">{{ showAddTaskPanel ? 'Cancel' : 'Add New Task' }}</Button>
    </div>
</template>

<script>
import './Header.scss';
import Button from '../Button/Button.vue';
export default {
    name: 'Header',
    props: {
        title: String,
        showAddTaskPanel: Boolean
    },
    components: {
        Button
    },
    emits: ['button-clicked']
}
</script>