<template>
  <div id="app">
    <img src="./assets/logo.png">
    <ToDoList/>
  </div>
</template>

<script>
import ToDoList from './components/todolist'

export default {
  name: 'App',
  components: {
    ToDoList
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
