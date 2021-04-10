<template>
<div class="container">
  <Header title="Task Tracker" />
  <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks" />
</div>
</template>

<script>
import Header from './components/Header'
import Tasks from './components/Tasks'
export default {
  name: 'App',
  components: {
    Header,
    Tasks,
  },
  data() {
    return {
      tasks: []
    }
  },
  methods: {
    deleteTask(id) {
      this.tasks = this.tasks.filter((task) => task.id !== id)
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map((task) => task.id === id ? {...task, reminder: !task.reminder } : task )
    }
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: 'Doctors Appointment',
        day: 'March 1st at 2:30pm',
        reminder: true,
      },
      {
        id: 2,
        text: 'Clinic Appointment',
        day: 'March 3rd at 8:30pm',
        reminder: true,
      },
      {
        id: 3,
        text: 'College Appointment',
        day: 'March 11th at 1:30am',
        reminder: false,
      }
    ]
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
