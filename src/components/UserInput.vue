<template>
    <div class="d-flex user-input-section ">
        <label><p>Enter something to do!</p></label>
        <input type="text" class="user-input" v-model="newTask" @keyup.enter="pushNewTask()">
        <button class="button" @click="pushNewTask">Add to List</button>
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