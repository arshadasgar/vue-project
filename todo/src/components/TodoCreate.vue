<template>
  <div class="col-md-12">
    <h3>Add task</h3>
    <div class="col-md-12">
      <input class="form-control" type="text" v-model="task" placeholder="Task title">
    </div>
    <div class="col-md-12">
      <button
        class="form-control btn btn-raised btn-primary"
        v-on:click="$emit('add-task-to-list', task)"
      >Add task</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "TodoCreate",
  data: function() {
    return {
      task: ""
    };
  },
  methods: {}
};
</script>