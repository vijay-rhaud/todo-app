<template>
    <div class="user-input-section d-flex">
        <input 
            placeholder="Enter something to do!" 
            type="text" 
            class="user-input" 
            v-model="newTask" 
            @keyup.enter="pushNewTask()"
        >
        <button class="button add" @click="pushNewTask()"><i class="fas fa-plus"></i></button>
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
    @import '../assets/styles/user-input.css';
</style>