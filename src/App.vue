<template>
  <div class="container">
    <HeaderComponent title="Task Tracker" @toggle-add-task="toggleAddTask" :showAddTask="showAddTask" />
    <div v-if="showAddTask">
      <AddTask @add-task="addTask" />
    </div>
    <TasksComponent @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks" />
  </div>
</template>

<script>
import HeaderComponent from "./components/Header.vue";
import TasksComponent from "./components/Tasks.vue";
import AddTask from "./components/AddTask.vue";

export default {
  name: "App",
  components: { HeaderComponent, TasksComponent, AddTask },
  data() {
    return {
      tasks: [],
      showAddTask: false,
    };
  },
  methods: {
    addTask(task) {
      this.tasks = [...this.tasks, task];
    },

    deleteTask(id) {
      if (confirm("Etes-vous sur ?")) {
        this.tasks = this.tasks.filter((task) => task.id !== id);
      }
    },

    toggleReminder(id) {
      this.tasks = this.tasks.map((task) => (task.id === id ? { ...task, reminder: !task.reminder } : task));
    },

    toggleAddTask() {
      this.showAddTask = !this.showAddTask;
    },
  },
  emits: ["delete-task", "toggle-reminder", "add-task"],
  created() {
    this.tasks = [
      {
        id: 1,
        text: "Doctors Appointment",
        day: "March 1st at 2:30pm",
        reminder: true,
      },
      {
        id: 2,
        text: "Meeting at School",
        day: "May 4th at 7:00pm",
        reminder: true,
      },
      {
        id: 3,
        text: "Learn the latest version of vue.js ",
        day: "October 22nd at 8:30am",
        reminder: false,
      },
    ];
  },
};
</script>

<style>
#app {
  max-width: 1280px;
  margin: 0 auto;
  padding: 2rem;

  font-weight: normal;
}

header {
  line-height: 1.5;
}
</style>
