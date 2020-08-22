<template>
    <div class="user-input-section">
        <input 
            placeholder="Enter something to do!" 
            type="text" 
            class="user-input" 
            v-model="newTask" 
            @keyup.enter="pushNewTask()"
        >
        <button class="" @click="pushNewTask()"><i class="fas fa-plus"></i></button>
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
.d-flex .user-input-section {
    margin-bottom: 40px;
}
.user-input {
    width: 400px;
    height: 24px;
}
</style>