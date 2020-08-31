<template>
    <div class="task-list d-flex">
        <div class="task" v-for="(task, index) in todoList" :key="index">
            <div class="task-view" v-if="editing !== index">
                <div class="task-checkbox">
                    <input
                        class="checkbox"
                        type="checkbox"
                        @click="completeTask(index)"
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
                        @input="updateTask(index)"
                        @keyup.enter="editTask()"
                        maxlength="300"
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
        updateTask(index) {
            this.$emit('updateTask', index);
        },
        completeTask(index) {
            this.$emit('completeTask', index);
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
    @import './todo-list.css';
</style>