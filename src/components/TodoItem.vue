<template>
  <li class="todo">
    <span class="todo-body">{{ todoText }}</span>
    <button class="check-btn">
      <i class="fas fa-check"></i>
    </button>
    <button class="delete-btn">
      <i class="far fa-trash-alt"></i>
    </button>
  </li>
</template>
<script>
export default {
  props: {
    todoText: {
      type: String,
      required: true,
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
}

.check-btn {
  background: #356cb6;
  margin-right: 10px;
}
.delete-btn {
  background: rgb(241, 148, 95);
}
</style>
