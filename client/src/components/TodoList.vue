<template>
    <ul>
      <TodoItem v-for="task in tasks" :key="task.id" :task="task" @toggle="toggle(task.id)" @remove="remove(task.id)" />
    </ul>
  </template>
  
  <script>
  import TodoItem from './TodoItem.vue';
  
  export default {
    props: ['tasks'],
    components: {
      TodoItem
    },
    methods: {
      toggle(taskId) {
        this.$emit('toggle', taskId);
      },
      remove(taskId) {
        this.$emit('remove', taskId);
      }
    }
  };
  </script>
  