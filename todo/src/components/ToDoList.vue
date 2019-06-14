<template>
  <div class="row">
    <div class="col-md-4">
      <div class="card">
        <TodoCreate v-on:add-task-to-list="addTask"/>
      </div>
    </div>
    <div class="text-left col-md-4">
      <div class="card">
        <h3 class="text-center">Pending tasks</h3>
        <ul>
          <li v-for="todo in todolist" v-bind:key="todo.id">
            <span>{{ todo.title }}</span>
            <span class="btn btn-success" v-on:click="markAsCompleted(todo.id)">
              <i>✔</i>
            </span>
          </li>
        </ul>
      </div>
    </div>
    <div class="col-md-4">
      <div class="card">
        <TodoCompleted v-bind:completedtasks="completedTasks"/>
      </div>
    </div>
  </div>
</template>

<script type = "text/javascript" >
import TodoCreate from "./TodoCreate";
import TodoCompleted from "./TodoCompleted";
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
    },
    markAsCompleted: function(taskId) {
      this.completedTasks.push(_.find(this.todolist, {id: taskId}));
      _.remove(this.todolist, { id: taskId });
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