<template>
    <div class="list-items d-flex">
        <div class="list-item" v-for="(items, index) in todoList" :key="items">
            <textarea 
                class="item"
                :class="{active: isActive}"
                type="text"
                :id='index'
                :value="items"
                :disabled="inputIsDisable"
                @keyup.enter="updateTask(items, index)"
            >
            </textarea>
            <button class="button-edit" @click="editTask()"><i class="fas fa-edit"></i></button>
            <button class="button-delete" @click="deleteTask(index)"><i class="fas fa-trash-alt"></i></button>
        </div>



<div style="display: flex; width: 100%;">
    <div style="width: 10%;">
        <input style="width: 100%;margin: 20px 0;" type="checkbox" id="vehicle1" name="vehicle1" value="Bike">
    </div>
    <div style="width: 70%; padding: 0 12px;">
        <input style="width: 100%;margin: 20px 0;">
    </div>
    <div style="display: flex; justify-content: flex-end; width:20%; padding-right: 12px;">
        <button style="width: 100%;margin: 20px 0;"><i class="fas fa-edit"></button>
        <button style="width: 100%;margin: 20px 0;"><i class="fas fa-trash-alt"></button>
    </div>
</div>





    </div>
</template>

<script>
export default {
    data() {
        return {
            inputIsDisable: true
        }
    },
    props: ['todoList'],
    methods: {
        editTask() {
            this.inputIsDisable = !this.inputIsDisable;
        },
        updateTask(items, index) {                  
            this.todoList.splice(index, 1, event.target.value);
        },
        deleteTask(index) {
            this.$emit('deleteTask', index);            
        }
    }
}
</script>

<style scoped>
.list-items {

}
.list-item {
    background-color: #fff;
    padding: 20px 8px;
    border-bottom: 2px solid #eee;
    width: 100%;
}
.list-item:first-child {
    border-top: 2px solid #eee;
}
.item {
    background-color: transparent;
    border: 1px solid transparent;
    color: #0353a4;
    font-family: 'Poppins', 'sans-serif';
    font-size: 16px;
}
.button-edit {
    background-color: #28a745;
    color: #fff;
    border: none;
    font-size: 12px;
    padding: 8px;
    border-radius: 4px;;
}
.button-edit:hover {
    background-color: #218838;
}
.button-delete {
    background-color: #dc3545;
    color: #fff;
    border: none;
    font-size: 12px;
    padding: 8px;
    border-radius: 4px;;
}
.button-delete:hover {
    background-color: #c82333;
}
</style>