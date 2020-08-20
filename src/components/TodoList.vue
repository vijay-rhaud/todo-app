<template>
    <div class="todo-list">



      <ol>
        <li v-for="items in todoList" :key="items"><p>{{ items }}</p></li>
      </ol>




    <div v-for="(items, index) in todoList" :key="items">
        <input :id='index' type="text" :value="items" disabled @keyup.enter="pushChangedTask(items, index)">
        <button @click="editTask(index)">Edit</button>
        <button @click="saveChanges(items, index)">Save Changes</button>
        <button>Delete</button>

    </div>






    </div>
</template>

<script>
export default {
    props: ['todoList'],
    data() {
        return {
            updatedTask: ''
        }
    },
    methods: {
        editTask(index) {
            document.getElementById(index).disabled = false;
        },
        saveChanges(items, index){
            document.getElementById(index).disabled = true;
            console.log(items)
        }










    }
}
</script>

<style scoped>
.todo-list {
  color: #023e7d;
}
</style>