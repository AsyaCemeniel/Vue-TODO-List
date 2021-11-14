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
      if (todo.todoText) {
        this.todos = [...this.todos, todo];
      }
    },
    deleteTodo(todo) {
      this.todos = this.todos.filter((t) => t.id !== todo.id);
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
    },
  },
  watch: {
    todos(newValue) {
      localStorage.setItem("todos", JSON.stringify(newValue));
      this.filterTodo(this.selected);
    },
  },
  mounted() {
    const todosFromStorage = JSON.parse(localStorage.getItem("todos"));
    if (todosFromStorage) {
      this.todos = todosFromStorage;
    }
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
  transition: 0.3s;
}

.tittle span {
  font-size: 60px;
  color: #356cb6;
  font-weight: bold;
  transition: 0.3s;
}

@media screen and (max-width: 500px) {
  .tittle {
    font-size: 35px;
    margin: 50px 0 30px 0;
  }
  .tittle span {
    font-size: 45px;
  }
}
</style>
