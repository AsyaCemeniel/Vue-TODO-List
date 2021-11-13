<template>
  <div class="todo-list" v-if="todos.length > 0">
    <ul>
      <transition-group name="todo-list">
        <TodoItem
          v-for="todo in todos"
          :todo="todo"
          :key="todo.id"
          @remove="$emit('remove', todo)"
          @checkTodo="checkTodo"
        />
      </transition-group>
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
.todo-list-item {
  display: inline-block;
  margin-right: 10px;
}
.todo-list-enter-active,
.todo-list-leave-active {
  transition: all 0.4s ease;
}
.todo-list-enter-from {
  opacity: 0;
  transform: translateX(130px);
}
.todo-list-leave-to {
  transform: translateY(8rem) rotate(20deg);
  opacity: 0;
}
.todo-list-move {
  transition: transform 0.4s ease;
}

@media screen and (max-width: 820px) {
  .todo-list {
    width: 85%;
  }
}
</style>
