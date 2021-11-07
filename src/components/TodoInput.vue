<template>
  <div class="container">
    <input v-model="todo.todoText" type="text" class="todo-input" autofocus />
    <button class="todo-button" type="submit" @click="createTodo">
      <i class="fas fa-plus-circle"></i>
    </button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      todo: {
        todoText: "",
        id: "",
        isChecked: false,
      },
    };
  },
  methods: {
    createTodo() {
      this.todo.id = Date.now();
      this.$emit("create", this.todo);
      this.todo = {
        todoText: "",
      };
    },
  },
};
</script>

<style scoped>
.container {
  display: flex;
  width: 70%;
  transition: 0.3s;
}
.todo-input {
  background: #eefffa;
  width: 85%;
  padding: 8px 15px;
  border-radius: 4px 0 0 4px;
}
.todo-button {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 15%;
  background: #eefffa;
  cursor: pointer;
  transition: all 0.2s ease;
  border-radius: 0 4px 4px 0;
  margin-right: 5px;
  transition: 0.3s;
}

.todo-input,
.todo-button {
  outline: none;
  font-size: 30px;
  border: none;
  color: #356cb6;
}

.todo-button:hover {
  background: #356cb6;
  color: #eefffa;
}

@media screen and (max-width: 820px) {
  .container {
    width: 100%;
    margin-bottom: 5px;
  }
  .todo-button {
    margin-right: 0;
  }
}
</style>
