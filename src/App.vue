<template>
  <div class="app">
    <div class="tittle">Your <span>ToDo</span> List</div>
    <TodoForm />
  </div>
</template>

<script>
import TodoForm from "./components/TodoForm";

export default {
  components: {
    TodoForm,
  },
};
</script>

<style></style>
