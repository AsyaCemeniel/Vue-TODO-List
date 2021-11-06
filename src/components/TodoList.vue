<template>
  <div v-if="todos.length > 0">
    <ul>
      <TodoItem
        v-for="todo in todos"
        :todoText="todo.todoText"
        :key="todo.id"
      />
    </ul>
  </div>
</template>
<script>
import TodoItem from "./TodoItem";

export default {
  components: { TodoItem },
  props: {
    todos: {
      type: Array,
      required: true,
    },
  },
};
</script>
<style scoped></style>
