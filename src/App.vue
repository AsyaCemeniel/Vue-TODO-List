<template>
  <div class="app">
    <div class="tittle">Your <span>ToDo</span> List</div>
    <TodoForm @create="createTodo" @filtertodo="filterTodo" />
    <TodoList
      :todos="filteredTodos"
      @remove="deleteTodo"
      @checkTodo="checkTodo"
    />
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
      filteredTodos: [],
      selected: "All",
    };
  },
  methods: {
    createTodo(todo) {
      this.todos.push(todo);
      this.filterTodo(this.selected);
    },
    deleteTodo(todo) {
      this.todos = this.todos.filter((t) => t.id !== todo.id);
      this.filterTodo(this.selected);
    },
    filterTodo(selected) {
      this.selected = selected;
      if (selected === "Completed") {
        this.filteredTodos = this.todos.filter((todo) => todo.isChecked);
      } else if (selected === "Uncompleted") {
        this.filteredTodos = this.todos.filter((todo) => !todo.isChecked);
      } else {
        this.filteredTodos = this.todos;
      }
    },
    checkTodo(updatedTodo) {
      this.todos = this.todos.map((todoItem) => {
        if (updatedTodo.id === todoItem.id) {
          return {
            ...todoItem,
            isChecked: updatedTodo.isChecked,
          };
        }
        return todoItem;
      });

      this.filterTodo(this.selected);
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
