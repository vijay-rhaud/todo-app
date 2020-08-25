<template>
    <div class="list-items d-flex">
        <div class="task" v-for="(task, index) in todoList" :key="index">
            <div class="task-view" v-if="editing !== index">
                <div class="task-checkbox">
                    <input
                        class="checkbox"
                        type="checkbox"
                        @click="completeTask(index, task)"
                        :checked="task.isComplete"
                    >
                </div>
                <div class="task-description">
                    <p
                        class="description"
                        @click="editTask(index)"
                        :class="{'task-is-completed': task.isComplete}"
                    >
                        {{task.description}}
                    </p>
                </div>
                <div class="task-delete">
                    <button class="button delete" @click="deleteTask(index)">
                        <i class="fas fa-times"></i>
                    </button>
                </div>
            </div>
            <div v-else class="task-edit">
                <div class="task-edit-input">
                    <input
                        class="task-input"
                        type="text"
                        :id="index"
                        :value="task.description"
                        @input="updateTask(index, task)"
                        @keyup.enter="editTask()"
                    >
                </div>
                <div class="task-save-button">
                    <button class="button save" @click="editTask()">
                        <i class="fas fa-save"></i>
                    </button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            editing: ''
        }
    },
    props: ['todoList'],
    methods: {
        updateTask(index, task) {
            this.$emit('updateTask', index, task);
        },
        saveTask() {
            this.activeIndex = ''
        },
        completeTask(index, task) {
            this.$emit('completeTask', index, task);
        },
        deleteTask(index) {
            this.$emit('deleteTask', index);
        },
        editTask(index) {
            this.editing = index;
        }
    }
}
</script>

<style scoped>
    @import '../assets/styles/todo-list.css';
</style>