<template>
  <div class="todo-app d-flex">
    <app-header></app-header>
    <app-user-input @addNewTaskToList="pushUserInput"></app-user-input>
    <app-todo-list 
      :todoList="todoList"
      @updateTask="updateTaskInArray"
      @deleteTask="deleteTaskFromArray"
      @completeTask="completeTaskInArray"
    >
    </app-todo-list>
  </div>
</template>
<script>
  import Header from './components/Header.vue';
  import UserInput from './components/UserInput.vue';
  import TodoList from './components/TodoList.vue';
  export default {
    data() {
      return {
        todoList: [
          {description: 'Learn Vue.js', isComplete: false},
          {description: 'Make Todo List Application', isComplete: false},
          {description: 'Learn Laravel', isComplete: false},

        ],
        maxTasks: 10,
      }
    },
    methods: {
      pushUserInput(newTask) {
        if (this.todoList.length >= this.maxTasks) {
          return alert("You're not able to do more than 10 tasks at a time!");
        }
        this.todoList.push({description: newTask, isComplete: false});
      },
      updateTaskInArray(index, task) {
        this.todoList.splice(index, 1, {description: event.target.value, isComplete: false});
      },
      completeTaskInArray(index, task) {
        this.todoList[index].isComplete = !this.todoList[index].isComplete
      },      
      deleteTaskFromArray(index) {
        this.todoList.splice(index, 1);
      }
    },
    components: {
      appHeader: Header,
      appUserInput: UserInput,
      appTodoList: TodoList
    }
  }
</script>
<style>
  @import './assets/styles/global.css';
</style>