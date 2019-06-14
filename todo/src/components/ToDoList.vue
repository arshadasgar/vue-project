<template>
  <div>
    <div class="card">
      <TodoCreate v-on:add-task-to-list="addTask"/>
    </div>
    <div class="card text-left">
      <h3>List</h3>
      <ul>
        <li v-for="todo in todolist" v-bind:key="todo.id">{{ todo.title }}</li>
      </ul>
    </div>
    <div>
      <TodoCompleted v-bind:completed-tasks="completedTasks" />
    </div>
  </div>
</template>

<script type = "text/javascript" >
import TodoCreate from "./TodoCreate";
import TodoCompleted from './TodoCompleted'
export default {
  data: function() {
    return {
      todolist: [
        {
          id: 1,
          title: "Todo A",
          project: "Project A",
          done: false
        },
        {
          id: 2,
          title: "Todo B",
          project: "Project B",
          done: true
        },
        {
          id: 3,
          title: "Todo C",
          project: "Project C",
          done: false
        },
        {
          id: 4,
          title: "Todo D",
          project: "Project D",
          done: false
        }
      ],
      completedTasks: [
        {
          id: 11,
          title: "Todo Dsdasd",
          project: "Project D",
          done: true
        }
      ]
    };
  },
  components: {
    TodoCreate,
    TodoCompleted
  },
  methods: {
    addTask: function(task) {
      let id = _.last(this.todolist).id + 1;
      this.todolist.push({ id: id, title: task, done: false });
    }
  }
};
</script>
<style>
.card {
  padding: 20px;
  background-color: white;
  margin-bottom: 10px;
}
</style>