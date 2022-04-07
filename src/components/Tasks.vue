<template>
  <div v-for="task in tasks" :key="task.id">
    <TaskItem :task="task" @toggle-reminder="$emit('toggle-reminder', task.id)" @delete-task="$emit('delete-task', task.id)" />
  </div>
</template>

<script>
import TaskItem from "./Task.vue";

export default {
  name: "TasksComponent",
  props: {
    tasks: Array,
  },
  components: {
    TaskItem,
  },
  methods: {},
  emits: ["delete-task", "toggle-reminder"],
};
</script>
