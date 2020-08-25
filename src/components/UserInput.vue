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
.d-flex .user-input-section {
    flex-direction: row;
    width: 100%;
    margin-bottom: 60px;
}
.user-input {
    width: 400px;
    height: 32px;
    margin-right: 16px;
    padding: 0;
    text-align: center;
    font-size: 16px;
    color: #000;
    font-family: 'Poppins', 'sans-serif';
}
.user-input::placeholder {
    font-size: 16px;
    color: #999;
    font-family: 'Poppins', 'sans-serif';
    text-align: center;
}
.add {
    background-color: #0466c8;
}
.add:hover {
    background-color: #0353a4;
}
</style>