<template>
    <div class="add-task-section d-flex">
        <input 
            placeholder="Enter a task here!" 
            type="text" 
            class="add-task" 
            v-model="newTask" 
            @keyup.enter="pushNewTask()"
        >
        <button 
            class="button add" 
            @click="pushNewTask()"
        >
            <i class="fas fa-plus"></i>
        </button>
    </div>
</template>

<script>
export default {
    data() {
        return {
            newTask: '',
        }
    },
    methods: {
        pushNewTask() {
            if (this.newTask == '') {
                return alert("Please enter in a task!");
            } else {
                this.$emit('addNewTaskToList', this.newTask);
                this.newTask = '';
            }
        }
    }
}
</script>

<style scoped>
    @import '../assets/styles/add-task.css';
</style>