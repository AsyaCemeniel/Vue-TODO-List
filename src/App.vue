<template>
  <div class="app">
    <div class="tittle">Your <span>ToDo</span> List</div>
    <TodoForm @create="createTodo" />
    <TodoList :todos="todos" />
  </div>
</template>

<script>
import TodoForm from "./components/TodoForm";
import TodoList from "./components/TodoList";

export default {
  components: {
    TodoForm,
    TodoList,
  },
  data() {
    return {
      todos: [],
    };
  },
  methods: {
    createTodo(todo) {
      this.todos.push(todo);
    },
  },
};
</script>

<style scoped>
.app {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.tittle {
  font-size: 50px;
  margin: 100px 0 30px 0;
}

.tittle span {
  font-size: 60px;
  color: #356cb6;
  font-weight: bold;
}
</style>
