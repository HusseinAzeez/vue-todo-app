<template>
  <div class="header">
    <h1>Todo List</h1>
    <div id="nav">
      <router-link to="/">Home</router-link>
      <router-link to="/about">About</router-link>
    </div>
  </div>
</template>


<script>
export default {
  name: "Header"
};
</script>

<style scoped>
.header {
  padding: 10px;
  text-align: center;
  color: #fff;
  background-color: #333;
}
.header a {
  color: #fff;
  padding-right: 5px;
  text-decoration: none;
}
</style>
