<!-- src/components/TodoItem.vue -->
<template>
    <li>
      <input type="checkbox" :checked="todo.completed" @change="toggleTodo" />
      {{ todo.text }}
      <button @click="remove">Remove</button>
    </li>
  </template>
  
  <script>
  export default {
    props: {
      todo: Object,
    },
    methods: {
      toggleTodo() {
        // Emit an event to request a change to the prop's value
        this.$emit("toggle", this.todo);
      },
      remove() {
        this.$emit("remove");
      },
    },
  };
  </script>
  