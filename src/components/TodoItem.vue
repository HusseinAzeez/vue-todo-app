<template>
  <div class="todo-item" v-bind:class="{'is-completed':todo.completed}">
    <p>
      <input type="checkbox" v-on:change="handleComplete">
      {{todo.title}}
      <button
        type="button"
        class="delete"
        v-on:click="$emit('del-todo', todo.id)"
      >x</button>
    </p>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo"],
  methods: {
    handleComplete() {
      this.todo.completed = !this.todo.completed;
    }
  }
};
</script>

<style scoped>
.todo-item {
  padding: 10px;
  border-bottom: 1px dotted #ccc;
  background-color: #f4f4f4;
}

.is-completed {
  text-decoration: line-through;
}

.delete {
  float: right;
  padding: 5px 9px;
  color: #fff;
  border: none;
  border-radius: 50%;
  cursor: pointer;
  background-color: #ff0000;
}
</style>
