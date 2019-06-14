<template>
    <div>
        <h3>Completed tasks</h3>
        <ul>
            <li vi-for="task in completed-tasks" vi-bind:key="task.id">{{ task.name }}</li>
        </ul>
    </div>
</template>
<script>
export default {
    name: "TodoCompleted",
    props: ['completed-tasks']
}
</script>