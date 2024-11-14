<template>
    <li :class="{ completed: task.completed }">
      <span @click="toggle">{{ task.text }}</span>
      <button @click="remove">Eliminar</button>
    </li>
  </template>
  
  <script>
  export default {
    props: ['task'],
    methods: {
      toggle() {
        this.$emit('toggle');
      },
      remove() {
        this.$emit('remove');
      }
    }
  };
  </script>
  
  <style scoped>
  .completed {
    text-decoration: line-through;
  }
  </style>
  