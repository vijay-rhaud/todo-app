<template>
  <div class="d-flex">
    <!------ Header ------>
    <app-header></app-header>

    <!------ User Input ------>
    <app-user-input @addNewTaskToList="pushUserInput"></app-user-input>

    <!------ Todo List ------>
    <app-todo-list :todoList="todoList"></app-todo-list>
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
          'Learn Vue', 
          'Make Todo List App', 
          'Learn Laravel'
        ],
        maxTasks: 10,
      }
    },
    methods: {
      pushUserInput(newTask) {
        if (this.todoList.length >= this.maxTasks) {
            return alert("You're not able to do more than 10 tasks at a time!");
        }
        this.todoList.push(newTask);
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
/** Global Styles **/
h1, h2, h3, h4, h5, h6, p, ol, li, a {
  font-family: 'Poppins', 'sans-serif'
}
.d-flex {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 100%;
}
.button {
  margin-top: 24px;
  background-color: #0353a4;
  border: 0px none transparent;
  border-radius: 8px;
  color: #fff;
  width: 240px;
  height: 40px;
  font-family: 'Poppins', 'sans-serif';
  font-size: 16px;
}
.button:focus {
  border-radius: 0px;
  outline: 4px solid #000;
}
</style>
