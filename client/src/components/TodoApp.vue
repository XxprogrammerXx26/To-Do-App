<template>
    <div class="todo-app">
      <h1>To-Do List</h1>
      <input v-model="newTask" placeholder="Añadir tarea..." @keyup.enter="addTask" />
      <button @click="addTask">Agregar</button>
  
      <TodoList :tasks="tasks" @toggle="toggleTask" @remove="removeTask" />
    </div>
  </template>
  
  <script>
  import TodoList from './TodoList.vue';
  
  export default {
    components: {
      TodoList
    },
    data() {
      return {
        newTask: '',
        tasks: []
      };
    },
    methods: {
      addTask() {
        if (this.newTask.trim() !== '') {
          this.tasks.push({
            id: Date.now(),
            text: this.newTask,
            completed: false
          });
          this.newTask = '';
        }
      },
      toggleTask(taskId) {
        const task = this.tasks.find(task => task.id === taskId);
        if (task) task.completed = !task.completed;
      },
      removeTask(taskId) {
        this.tasks = this.tasks.filter(task => task.id !== taskId);
      }
    }
  };
  </script>
  
  <style scoped>
  .todo-app {
    max-width: 400px;
    margin: 0 auto;
    text-align: center;
  }
  </style>
  