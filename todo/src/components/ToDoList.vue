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
            <span class="btn btn-success" v-on:click="markAsCompleted(todo)">
              <i>✔</i>
            </span>
          </li>
        </ul>
      </div>
    </div>
    <div class="col-md-4">
      <div class="card">
        <TodoCompleted
          v-bind:completedtasks="completedTasks"
          v-on:markasnotcompleted="markAsNotCompleted"
        />
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
          done: false
        },
        {
          id: 2,
          title: "Todo B",
          done: true
        },
        {
          id: 3,
          title: "Todo C",
          done: false
        },
        {
          id: 4,
          title: "Todo D",
          done: false
        }
      ],
      completedTasks: []
    };
  },
  components: {
    TodoCreate,
    TodoCompleted
  },
  methods: {
    addTask: function(task) {
      let id = (!_.isEmpty(this.todolist)) ? _.last(this.todolist).id + 1 : 1;
      this.todolist.push({ id: id, title: task, done: false });
    },
    markAsCompleted: function(task) {
      this.completedTasks.push(task);
      _.remove(this.todolist, task);
    },
    markAsNotCompleted: function(task) {
      this.todolist.push(task);
      _.remove(this.completedTasks, task);
      this.$forceUpdate();
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