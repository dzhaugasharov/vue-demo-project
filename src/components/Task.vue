<template>
    <div :class="`task ${task.completed ? 'completed' : ''}`">
        <h4>{{ task.title }}</h4>
        <label><input type="checkbox" v-model="task.completed"> completed</label>
        <div>{{ task.description }}</div>
        <a href="#" @click.prevent="$emit('delete-task', task)">delete</a>
    </div>
</template>

<script>

export default {
    props: ['task'],
    data() {
        return {

        }
    }
}
</script>