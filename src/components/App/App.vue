<template>
  <div class="container">
    <Header title="VueJS ToDo List Application" />
    <Tasks :tasks="tasks" />
  </div>
</template>

<script>
import './App.scss';
import Header from '../Header/Header.vue';
import Tasks from '../Tasks/Tasks.vue';
export default {
  name: 'App',
  components: {
    Header,
    Tasks
  },
  data() {
    return {
      tasks: []
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