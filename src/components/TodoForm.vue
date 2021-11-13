<template>
  <form class="todo-form" @submit.prevent>
    <TodoInput @create="createTodo" />
    <v-select
      v-model="selected"
      class="oktopost"
      :options="options"
      placeholder="Filter"
      @option:selected="filterTodo"
    ></v-select>
  </form>
</template>

<script>
import TodoInput from "./TodoInput";

export default {
  data() {
    return {
      options: ["All", "Completed", "Uncompleted"],
      selected: "All",
    };
  },
  components: {
    TodoInput,
  },
  methods: {
    createTodo(todo) {
      this.$emit("create", todo);
    },
    filterTodo() {
      this.$emit("filtertodo", this.selected);
    },
  },
};
</script>

<style>
.todo-form {
  display: flex;
  width: 700px;
  align-items: center;
  margin-bottom: 40px;
  transition: 0.3s;
}

.oktopost.v-select {
  width: 30%;
  height: 50px;
  transition: 0.3s;
}

.oktopost .vs__search,
.oktopost .vs__dropdown-toggle,
.oktopost .vs__dropdown-menu {
  background: #eefffa;
  color: #b4b4b4;
}

.oktopost .vs__search,
.oktopost .vs__dropdown-toggle {
  height: 100%;
}

.oktopost .vs__selected,
.oktopost li {
  color: #356cb6;
}

.oktopost .vs__clear {
  display: none;
}
.oktopost .vs__actions {
  cursor: pointer;
  padding: 4px 10px 0 10px;
}

@media screen and (max-width: 820px) {
  .todo-form {
    flex-direction: column;
    width: 85%;
  }
  .oktopost.v-select {
    width: 100%;
  }
}
</style>
