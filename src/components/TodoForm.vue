<template>
  <form class="todo-form">
    <TodoInput />
    <v-select
      class="oktopost"
      :options="options"
      placeholder="Filter"
    ></v-select>
  </form>
</template>

<script>
import TodoInput from "./TodoInput";

export default {
  data() {
    return {
      options: ["All", "Completed", "Uncompleted"],
    };
  },
  components: {
    TodoInput,
  },
};
</script>

<style>
.todo-form {
  display: flex;
  width: 700px;
  align-items: center;
}

.oktopost.v-select {
  width: 30%;
  height: 50px;
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
</style>
