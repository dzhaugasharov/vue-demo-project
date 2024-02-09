<template>
    <form @submit.prevent="addTask()" class="task-form">
        <div>
            <label for="title">Task name</label>
            <input type="text" id="title" v-model="title">
        </div>
        <div>
            <label for="desc">Task description</label>
            <input type="text" id="desc" v-model="description">
        </div>
        <input type="submit" value="add">
    </form>
</template>

<script>

export default {
    data() {
        return {
            title: null,
            description: null
        }
    },
    methods: {
        addTask() {
            if (!this.title) {
                return;
            }
            this.$emit('add-task', this.title, this.description);
            this.title = null;
            this.description = null;
        }
    }
}
</script>

<style lang="scss">
.task-form {
    margin-top: 20px;
}
</style>