<template>
  <div class="container">
    <Header @button-clicked="toggleAddTaskPanel" :showAddTaskPanel="showAddTaskPanel" title="VueJS ToDo List Application" />
    <AddTaskPanel @add-task="addTask" @hide-add-task-panel="toggleAddTaskPanel" :showAddTaskPanel="showAddTaskPanel" />
    <Tasks @delete-task="deleteTask" @toggle-reminder="toggleReminder" :tasks="tasks" />
  </div>
</template>

<script>
import './App.scss';
import Header from '../Header/Header.vue';
import Tasks from '../Tasks/Tasks.vue';
import AddTaskPanel from '../AddTaskPanel/AddTaskPanel.vue';

export default {
  name: 'App',
  components: {
    Header,
    Tasks,
    AddTaskPanel
  },
  methods: {
    deleteTask(id) {
      if( confirm('Are you sure, you want to delete this task ?') )
        this.tasks = this.tasks.filter(task => task.id !== id);
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map(task => task.id === id ? { ...task, reminder: !task.reminder } : task);
    },
    addTask(task) {
      this.tasks = [task, ...this.tasks];
    },
    toggleAddTaskPanel() {
      this.showAddTaskPanel = !this.showAddTaskPanel;
    }
  },
  data() {
    return {
      tasks: [],
      showAddTaskPanel: false
    }
  },
  created() {
    this.tasks = [
    {
      "id": "1",
      "text": "Doctors Appointment",
      "day": "March 5th at 2:30pm",
      "reminder": true
    },
    {
      "id": "2",
      "text": "Meeting with boss",
      "day": "March 6th at 1:30pm",
      "reminder": true
    },
    {
      "id": "3",
      "text": "Food shopping",
      "day": "March 7th at 2:00pm",
      "reminder": false
    }
  ]
  }
}
</script>