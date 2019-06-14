<template>
  <div>
    <h3>Add task</h3>  
    <input class="form-control" type="text" v-model="task">
    <button class="form-control btn btn-success" v-on:click="$emit('add-task-to-list', task)">Add task</button>
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
  methods: {
  }
};
</script>