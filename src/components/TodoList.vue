<template>
  <div class="todo-list" v-if="todos.length > 0">
    <ul>
      <TodoItem
        v-for="todo in todos"
        :todo="todo"
        :key="todo.id"
        @remove="$emit('remove', todo)"
        @checkTodo="checkTodo"
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
  methods: {
    checkTodo(updatedTodo) {
      this.$emit("checkTodo", updatedTodo);
    },
  },
};
</script>
<style scoped>
@media screen and (max-width: 820px) {
  .todo-list {
    width: 85%;
  }
}
</style>
