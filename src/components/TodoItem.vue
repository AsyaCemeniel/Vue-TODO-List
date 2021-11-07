<template>
  <li class="todo">
    <span class="todo-body" :class="{ done: isChecked }">{{
      todo.todoText
    }}</span>
    <button class="check-btn" @click="toggleDone">
      <i class="fas fa-check"></i>
    </button>
    <button class="delete-btn" @click="$emit('remove', todo)">
      <i class="far fa-trash-alt"></i>
    </button>
  </li>
</template>
<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      isChecked: this.$props.todo.isChecked,
    };
  },
  methods: {
    toggleDone() {
      const newValue = !this.isChecked;
      const updatedTodo = { ...this.todo, isChecked: newValue };
      this.$emit("checkTodo", updatedTodo);
      this.isChecked = newValue;
    },
  },
};
</script>
<style scoped>
.todo {
  display: flex;
  align-items: center;
  margin-bottom: 15px;
}
.todo-body {
  width: 590px;
  background: #eefffa;
  color: #356cb6;
  font-size: 25px;
  padding: 8px 15px;
  border-radius: 8px;
  margin-right: 10px;
  word-break: break-all;
}

.done {
  text-decoration: line-through;
  opacity: 0.5;
}

button {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 45px;
  height: 45px;
  border-radius: 50%;
  border: none;
  cursor: pointer;
  font-size: 25px;
  color: #eefffa;
  transition: 0.3s;
}

.check-btn {
  background: #356cb6;
  margin-right: 10px;
}
.check-btn:hover {
  background: #eefffa;
  color: #356cb6;
}

.delete-btn {
  background: rgb(241, 148, 95);
}
.delete-btn:hover {
  background: #eefffa;
  color: rgb(241, 148, 95);
}
</style>
