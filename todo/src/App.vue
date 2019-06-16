<template>
  <div id="app_div">
    <TodoList />
  </div>
</template>

<script>
import TodoList from './components/ToDoList'


export default {
  name: 'App',
  components: {
    TodoList
  },
  data: function() {
    return {
      
    }
  }
}
</script>

<style>
#app_div {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
