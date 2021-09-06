<template>
    <div class="AddTaskPanel">
        <form action="/">
            <Input mainlabel="Task Text" name="task-text" placeholder="Enter your task description" />
            <Input inputType="datetime-local" mainlabel="Task Date & Time" name="task-time" />
            <Input inputType="checkbox" mainlabel="Set a reminder" name="task-time" />
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
    }
}
</script>

<style scoped>
    button { margin: 0!important; margin-bottom: 15px!important; float: unset; width: 100%;  }
</style>