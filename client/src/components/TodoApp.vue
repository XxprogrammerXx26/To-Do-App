<template>
  <div class="todo-app">
    <h1>Agregar Tareas</h1>
    <input 
      v-model="newTask" 
      placeholder="Añadir tarea..." 
      @keyup.enter="addTask" 
      class="todo-input" 
    />
    <button @click="addTask" class="add-button">Agregar</button>

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
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html, body {
  height: 100%; /* Asegura que el body ocupe toda la altura de la pantalla */
  font-family: 'Roboto', sans-serif;
  display: flex;
  justify-content: center; /* Centrado horizontal */
  align-items: center; /* Centrado vertical */
  background-color: #f0f0f0;
}

.todo-app {
  max-width: 450px;
  width: 500%; /* Para que ocupe todo el espacio disponible en pantallas pequeñas */
  padding: 30px;
  background-color: #ffffff;
  border-radius: 10px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  text-align: center;
}

h1 {
  color: #4a4a4a;
  font-size: 2.5rem;
  margin-bottom: 20px;
}

.todo-input {
  width: 100%;
  padding: 15px;
  margin: 10px 0;
  border: 1px solid #ddd;
  border-radius: 5px;
  font-size: 1rem;
  transition: border-color 0.3s;
}

.todo-input:focus {
  outline: none;
  border-color: #007bff;
}

.add-button {
  padding: 12px 20px;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 5px;
  font-size: 1rem;
  cursor: pointer;
  transition: background-color 0.3s;
}

.add-button:hover {
  background-color: #0056b3;
}

ul {
  list-style: none;
  padding: 0;
  margin-top: 20px;
}

li {
  background-color: #fff;
  padding: 15px;
  margin: 10px 0;
  border-radius: 5px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  display: flex;
  justify-content: space-between;
  align-items: center;
  transition: background-color 0.3s;
}

li:hover {
  background-color: #f1f1f1;
}

button {
  background-color: #dc3545;
  color: white;
  border: none;
  padding: 5px 10px;
  border-radius: 5px;
  cursor: pointer;
  font-size: 0.9rem;
  transition: background-color 0.3s;
}

button:hover {
  background-color: #c82333;
}

.completed {
  text-decoration: line-through;
  color: #6c757d;
}
</style>