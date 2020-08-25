<template>
    <div class="list-items d-flex">
        <div class="list-item" v-for="(task, index) in todoList" :key="index">
            <div class="list-input-section">
                <input
                    class="list-checkbox"
                    type="checkbox"
                    @click="completeTask(index, task)"
                >
                <input
                    class="list-input"
                    :class="{'task-is-completed': task.isComplete}"
                    type="text"
                    :id="index"
                    :value="task.description"
                    :disabled="activeIndex !== index"
                    @input="updateTask(index, task)"
                >
            </div>
            <div class="list-button-section">
                <button class="button edit" @click="editTask(index);">
                    <i class="fas fa-edit"></i>
                </button>
                <button class="button save" @click="saveTask()">
                    <i class="fas fa-save"></i>
                </button>
                <button class="button delete" @click="deleteTask(index)">
                    <i class="fas fa-times"></i>
                </button>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            activeIndex: '',
            taskCompleted: false
        }
    },
    props: ['todoList'],
    methods: {
        editTask(index) {
            this.activeIndex = index;
        },
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
        }
    }
}
</script>

<style scoped>
  @import '../assets/styles/todo-list.css';
</style>