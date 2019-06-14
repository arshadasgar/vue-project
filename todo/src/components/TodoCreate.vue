<template>
  <div>
    <h3>Add task</h3>  
    <input type="text" v-model="task">
    <button v-on:click="$emit('add-task-to-list', task)">Add task</button>
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