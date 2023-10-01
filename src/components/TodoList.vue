
<template>
    <div class="todo-app">
        <img class="image" src="https://visitindependence.com/wp-content/uploads/2019/04/Things-to-Do.png" />
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
  
  <style scoped></style>
  