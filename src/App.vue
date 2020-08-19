<template>
  <div class="d-flex">
    <div class="header">
      <h1>Todo Application</h1>
    </div>
    <div class="d-flex user-input-section ">
      <label for="todo"><p>Enter something to do!</p></label>
      <input type="text" class="user-input" v-model="userInput">
      <button class="button" @click="pushUserInput">Add to List</button>
    </div>
    <div class="todo-list">
      <ol>
        <li v-for="items in todoList" :key="items"><p>{{ items }}</p></li>
      </ol>
    </div>
  </div>
</template>
<script>
  export default {
    data() {
      return {
        todoList: ['Get Money', 'Get Paid', 'Buy a Scirocco'],
        userInput: '',
        maxTasks: 10,
      }
    },
    methods: {
      pushUserInput() {
        if(this.todoList.length >= this.maxTasks) {
            return alert("You're not capable of doing more than 10 tasks at a time!");
        }
        if(this.userInput == '') {
          return alert("Please enter in a task!");
        }
        this.todoList.push(this.userInput);
        this.userInput = '';
      }
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
/** Header Section Styles **/
.header {
  width: 100%;

}
.header h1{
  text-align: center;
  font-size: 48px;
  color: #0353a4;
  text-transform: uppercase;
  margin-bottom: 20px;
}
/** User Input Section Styles **/
.d-flex .user-input-section {
  margin-bottom: 40px;
}
.user-input {
  width: 400px;
  height: 24px;
}
/** Todo List Section Styles **/
.todo-list {
  color: #023e7d;
}
</style>
