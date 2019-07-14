<template>
    <div class="task-grid">
        <template v-if="tasks.length">
            <Task v-for="(task, i) in tasks" :key="task.name"
                @taskStateChanged="taskStateChanged(i)"
                @taskDeleted="taskDeleted(i)"
                :task="task"></Task>
        </template>
        <p v-else class="no-task">Sua vida está em dia!!!</p>
    </div>
</template>

<script>
import Task from './Task.vue'

export default {
    components: { Task },

    props: {
        tasks: {
            type: Array,
            required: true
        }
    },
    methods: {
        taskDeleted(i) {
            this.$emit('taskDeleted', i)
        },
        taskStateChanged(i) {
            this.$emit('taskStateChanged', i)
        }
    }    
}
</script>

<style>
    .task-grid {
        display: flex;
        justify-content: center;
        flex-wrap: wrap;
    }

    .task-grid .task {
        margin: 5px;
    }

    .no-task {
        color: #000;
        font-size: 2.rem
    }
</style>
