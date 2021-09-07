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
import axios from 'axios';

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
    axios.get('https://todo-list-app-c2763-default-rtdb.firebaseio.com/tasks.json').then(respond => {
      if( respond ) {
        this.tasks = respond.data;
      }
    }).catch(error => console.log(error));
  }
}
</script>