<template>
  <div class="todo-app d-flex">
    <!------ Header ------>
    <app-header></app-header>

    <!------ User Input ------>
    <app-user-input @addNewTaskToList="pushUserInput"></app-user-input>

    <!------ Todo List ------>
    <app-todo-list :todoList="todoList" @deleteTask="deleteTaskFromArray"></app-todo-list>

    <button @click="test()">Test Button</button>
    {{todoList}}

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
          {task: 'Learn Vue.js', isComplete: false},
          {task: 'Make Todo App', isComplete: false},
          {task: 'Learn Laravel', isComplete: false}
        ],
        maxTasks: 10,
      }
    },
    methods: {
      pushUserInput(newTask) {
        if (this.todoList.length >= this.maxTasks) {
            return alert("You're not able to do more than 10 tasks at a time!");
        }
        this.todoList.push({task: newTask, isComplete: false});
      },
      deleteTaskFromArray(index) {
        this.todoList.splice(index, 1);
      },
      test() {
        console.log(this.todoList)
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
.todo-app {
  border: 8px solid #0353a4;
  border-radius: 25px;
  width: 60%;
  margin: 120px auto;
  padding-bottom: 120px;
}
.button {
  border: 0 none transparent;
  padding: 8px 12px;
  color: #fff;
  cursor: pointer;
  font-size: 16px;
  border-radius: 4px;
}
.button:hover {
  transition: 0.1s;
}
</style>
