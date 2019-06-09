<template>
  <div>
    <AddTodo v-on:add-todo="handleAddTodo"/>
    <TodosList v-bind:todos="todos" v-on:del-todo="handleDeleteTodo"/>
  </div>
</template>

<script>
// Third-party imports
import axios from "axios";
// Local imports
import TodosList from "../TodosList";
import AddTodo from "../AddTodo";

export default {
  name: "Home",
  components: {
    TodosList,
    AddTodo
  },
  async created() {
    const response = await axios.get(
      "https://jsonplaceholder.typicode.com/todos?_limit=10"
    );
    this.todos = response.data;
  },
  data() {
    return {
      todos: []
    };
  },
  methods: {
    handleDeleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
    async handleAddTodo(newTodo) {
      const { title, completed } = newTodo;
      const response = await axios.post(
        "https://jsonplaceholder.typicode.com/todos",
        {
          title,
          completed
        }
      );
      this.todos = [...this.todos, response.data];
    }
  }
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}
</style>
