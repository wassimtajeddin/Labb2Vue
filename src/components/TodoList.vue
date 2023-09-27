<!-- src/components/TodoList.vue -->
<template>
    <div class="todo-app">
      <h1>To-Do List</h1>
      <div class="input-container">
        <input v-model="newTodo" @keyup.enter="addTodo" placeholder="Add a new task" />
        <button @click="addTodo">Add</button>
      </div>
      <ul class="todo-list">
        <TodoItem v-for="(todo, index) in todos" :key="index" :todo="todo" @toggle="toggleTodo(index)" @remove="removeTodo(index)" />
      </ul>
    </div>
  </template>
  
  <script>
  import TodoItem from "./TodoItem.vue";
  
  export default {
    components: {
      TodoItem,
    },
    data() {
      return {
        newTodo: "",
        todos: [],
      };
    },
    methods: {
      addTodo() {
        if (this.newTodo.trim() !== "") {
          this.todos.push({ text: this.newTodo, completed: false });
          this.newTodo = "";
        }
      },
      toggleTodo(index) {
        this.todos[index].completed = !this.todos[index].completed;
      },
      removeTodo(index) {
        this.todos.splice(index, 1);
      },
    },
  };
  </script>
  
  <style scoped>
  .todo-app {
    font-family: Arial, sans-serif;
    text-align: center;
    max-width: 400px;
    margin: 0 auto;
    padding: 20px;
  }
  
  h1 {
    font-size: 28px;
    margin-bottom: 20px;
  }
  
  .input-container {
    display: flex;
    margin-bottom: 10px;
  }
  
  input[type="text"] {
    flex-grow: 1;
    padding: 10px;
    font-size: 16px;
    border: 1px solid #ccc;
    border-radius: 4px;
  }
  
  button {
    background-color: #007BFF;
    color: white;
    border: none;
    border-radius: 4px;
    padding: 10px 20px;
    font-size: 16px;
    cursor: pointer;
  }
  
  button:hover {
    background-color: #0056b3;
  }
  
  .todo-list {
    list-style: none;
    padding: 0;
  }
  
  li {
    display: flex;
    align-items: center;
    justify-content: space-between;
    background-color: #f9f9f9;
    border: 1px solid #ddd;
    border-radius: 4px;
    margin: 5px 0;
    padding: 10px;
  }
  
  input[type="checkbox"] {
    margin-right: 10px;
  }
  
  button.remove-button {
    background-color: #ff4500;
    color: white;
    border: none;
    border-radius: 4px;
    padding: 5px 10px;
    font-size: 12px;
    cursor: pointer;
  }
  
  button.remove-button:hover {
    background-color: #d13800;
  }
  </style>
  