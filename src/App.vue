<template>
  <div class="todo-app d-flex">
    <app-header></app-header>
    <app-new-task-input @addTask="addTask"></app-new-task-input>
    <app-todo-list 
      :todoList="todoList"
      @updateTask="updateTask"
      @deleteTask="deleteTask"
      @completeTask="completeTask"
    >
    </app-todo-list>
  </div>
</template>
<script>
  import Header from './components/Header/Header.vue';
  import NewTaskInput from './components/NewTaskInput/NewTaskInput.vue';
  import TodoList from './components/TodoList/TodoList.vue';

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
      addTask(newTask) {
        if (this.todoList.length >= this.maxTasks) {
          return alert("You're not able to do more than 10 tasks at a time!");
        }
        this.todoList.push({description: newTask, isComplete: false});
      },
      updateTask(index, task) {
        this.todoList.splice(index, 1, {description: event.target.value, isComplete: false});
      },
      completeTask(index, task) {
        this.todoList[index].isComplete = !this.todoList[index].isComplete
      },      
      deleteTask(index) {
        this.todoList.splice(index, 1);
      }
    },
    components: {
      appHeader: Header,
      appNewTaskInput: NewTaskInput,
      appTodoList: TodoList
    }
  }
</script>
<style>
  @import './assets/styles/global.css';
</style>