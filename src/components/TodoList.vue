<template>
    <div class="list-items d-flex">

        <!-- <ol style="border-bottom: 1px solid red;">
            <li v-for="items in todoList" :key="items"><p>{{ items }}</p></li>
        </ol> -->

        <!--- 
            REMEMBER THE FOLLOWING:
                . $event.target.value
                . $emit
                . @change
                . @input 
        -->

        <!-- <div class="list-item" v-for="(items, index) in todoList" :key="items">

            <div class="list-input-section">

                <input
                    class="list-checkbox"                
                    type="checkbox"
                    @click="taskCompleted = !taskCompleted"
                >

                <input
                    class="list-input"
                    :class="completedTask()"
                    type="text"
                    :id="index"
                    :value="items"
                    :disabled="activeIndex !== index"
                    @keyup.enter="updateTask(items, index)"
                >

            </div>
            
            <div class="list-button-section">

                <button class="button edit" @click="editTask(index);"><i class="fas fa-edit"></i></button>
                <button class="button save" @click="saveTask()"><i class="fas fa-edit"></i></button>
                <button class="button delete" @click="deleteTask(index)"><i class="fas fa-times"></i></button>

            </div>

        </div> -->
        

                <!-- :class="{red: taskCompleted} " -->

        <ol >
            <li 
                v-for="(task, index) in todoList" :key="index"
                :class="{red: taskCompleted} "                
            >

                {{task.description}}
                -----------------
                {{task.isComplete}}
                -----------------
                <button @click="completeTask(task, index)">Complete Task</button>

            </li>
        </ol>



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
        updateTask(items, index) {                  
            this.todoList.splice(index, 1, event.target.value);
            this.activeIndex = '';
        },
        deleteTask(index) {
            this.$emit('deleteTask', index);            
        },
        saveTask() {
            this.activeIndex = ''
        },
        completedTask() {
            return {
                'taskCompleted' : this.taskCompleted
            }
        },






        completeTask(task, index) {
            task.isComplete = !task.isComplete;
            console.log(index);
            console.log(task.description);
            console.log(task.isComplete);
        }







    }
}
</script>

<style scoped>
.list-items {
    padding-bottom: 80px;
}
.list-item {
    display: flex;    
    width: 100%;
    margin-bottom: 32px;
}
.list-input-section {
    display: flex; 
    justify-content: space-evenly;
    align-items: center;
    padding-left: 20px;
    width: 100%; 
    max-width: 70%; 
}
.list-input {
    width: 100%;
    max-width: 90%;
    font-size: 20px;
    font-family: 'Poppins', 'sans-serif';
    padding-left: 12px;
}
.task-is-completed {
    text-decoration: line-through;
}
.list-button-section {
    width: 30%;
    display: flex;
    justify-content: space-evenly; 
    padding-right: 20px;
}
.edit {
    background-color: #28a745;
}
.edit:hover {
    background-color: #218838;
}
.save {
    background-color: #ffc107;
}
.save:hover {
    background-color: #e0a800;
}
.delete {
    background-color: #dc3545;
}
.delete:hover {
    background-color: #c82333;
}


.red {
    background-color: red;
}

</style>