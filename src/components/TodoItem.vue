
<template>
    <li>
      <input type="checkbox" :checked="todo.completed" @change="toggleTodo" />
      {{ todo.text }}
      <button class="remove-button" @click="remove">Remove</button>
    </li>
  </template>
  
  <script>
  export default {
    props: {
      todo: Object,
    },
    methods: {
      toggleTodo() {
        this.$emit("toggle", this.todo);
      },
      remove() {
        this.$emit("remove");
      },
    },
  };
  </script>
  
  