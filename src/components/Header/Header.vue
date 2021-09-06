<template>
    <div class="Header">
        <div class="title"><h3>{{ title }}</h3></div>
        <Button className="button-success">Add New Task</Button>
    </div>
</template>

<script>
import './Header.scss';
import Button from '../Button/Button.vue';
export default {
    name: 'Header',
    props: {
        title: String
    },
    components: {
        Button
    }
}
</script>