<template>
    <div class="text-left">
        <h3 class="text-center">Completed tasks</h3>
        <ul>
            <li v-for="task in completedtasks" v-bind:key="task.id">{{ task.title }}</li>
        </ul>
    </div>
</template>
<script>
export default {
    name: "TodoCompleted",
    props: ['completedtasks']
}
</script>