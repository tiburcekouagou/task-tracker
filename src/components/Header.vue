<template>
  <header>
    <h1>{{ title }}</h1>
    <ButtonItem @btn-click="$emit('toggle-add-task')" :text="showAddTask ? 'Close' : 'Add Task'" :color="showAddTask ? 'red' : 'green'" />
  </header>
</template>

<script>
import ButtonItem from "./Button.vue";

export default {
  name: "HeaderComponent",
  props: {
    title: String,
    showAddTask: Boolean,
  },
  emits: ["toggle-add-task"],
  components: {
    ButtonItem,
  },
};
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
  border: 1px solid #ddd;
  padding-inline: 1.5rem;
}
</style>
