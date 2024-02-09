<template>
    <div>
        <h2 style="margin-bottom: 20px;">Tasks list</h2>
        <p>Completed: {{ totalCompleted }}</p>
        <div class="tasks">
            <task v-for="task in tasks" :task="task" :key="`item-${task.id}`" v-on:delete-task="deleteTask"></task>
        </div>

        <task-form v-on:addTask="addTask"></task-form>
    </div>
</template>

<script>
import Task from './Task.vue'
import TaskForm from './TaskForm.vue'

export default {
  components: { Task, TaskForm },
    data() {
        return {
            tasks: [{id: 1, title: 'TITLE', description: 'DESC'}]
        }
    },
    computed: {
        totalCompleted() {
            let total = 0;
            this.tasks.map(v => {
                if (v.completed) {
                    total++;
                }
            });
            return total;
        }
    },
    methods: {
        addTask(title, description) {
            this.tasks.splice(this.tasks.length, 0, {title: title, description: description});
        },
        deleteTask(task) {
            const i = this.tasks.indexOf(task);
            this.tasks.splice(i, 1);
        }
    }
}
</script>

<style lang="scss">
.tasks {
    &> div.task {
        border-bottom: 1px solid silver;
        &.completed {
            background-color: green;
        }
    }
}
</style>