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
    // Delete a task
    // First remove that task from the dom then make the hhtp request to the firebase database to delete it
    deleteTask(id) {
      if( confirm('Are you sure, you want to delete this task ?') ) {
        this.tasks = this.tasks.filter(task => task.id !== id);
        axios.delete(`https://todo-list-app-c2763-default-rtdb.firebaseio.com/tasks/${ id }.json`).catch(error => console.log(error));
      }
        
    },
    // Toggle reminder for a task
    // change the stste of the reminder to the reversed one then update firebase database
    toggleReminder(id) {
      this.tasks = this.tasks.map(task => {
        if (task.id === id) {
          task = { ...task, reminder: !task.reminder }
          axios.patch(`https://todo-list-app-c2763-default-rtdb.firebaseio.com/tasks/${ id }.json`, { reminder: task.reminder }).catch(error => console.log(error));
        }
        return task;
      });
    },
    // Add task
    // Insert that task to the dom then update firebase :)
    addTask(task) {
      this.tasks = [...this.tasks, task];
      axios.post('https://todo-list-app-c2763-default-rtdb.firebaseio.com/tasks.json', task).catch(error => console.log(error));
    },
    // Switch between the show and hide of the add task form
    toggleAddTaskPanel() { this.showAddTaskPanel = !this.showAddTaskPanel; }
  },
  data() {
    return {
      tasks: [],
      showAddTaskPanel: false
    }
  },
  // Get all tasks on component load
  created() {
    axios.get('https://todo-list-app-c2763-default-rtdb.firebaseio.com/tasks.json').then(respond => {
      if( respond ) {
        this.tasks = Object.keys( respond.data ).map( ( key ) => ({ ...respond.data[ key ], id: key }));
      }
    }).catch(error => console.log(error));
    
  }
}
</script>