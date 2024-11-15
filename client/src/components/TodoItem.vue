<template>
  <li :class="{ completed: task.completed }">
    <span @click="toggle" class="task-text">{{ task.text }}</span>
    <button @click="remove" class="remove-button">Eliminar</button>
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
/* Estilo para el texto de la tarea */
.task-text {
  display: inline-block;
  padding: 10px 15px;
  border: 2px solid #ccc;  /* Borde gris suave */
  border-radius: 5px;  /* Bordes redondeados */
  font-size: 16px;
  background-color: #f9f9f9;  /* Fondo gris claro */
  transition: all 0.3s ease; /* Transición suave para hover */
}

.task-text:hover {
  background-color: #e0e0e0; /* Fondo más oscuro al pasar el mouse */
  border-color: #999; /* Cambiar el color del borde al pasar el mouse */
}

.completed .task-text {
  text-decoration: line-through;
  color: #999;  /* Color gris claro para el texto completado */
}

/* Estilo para el botón de eliminar */
.remove-button {
  color: red;  /* Color rojo para el texto */
  background-color: white;  /* Fondo blanco para el botón */
  border: 2px solid red;  /* Borde rojo alrededor del botón */
  border-radius: 5px;  /* Bordes redondeados */
  cursor: pointer;
  font-weight: bold;
  margin-left: 10px;
  font-size: 14px;
  padding: 5px 10px;  /* Espaciado interno */
  transition: all 0.3s ease; /* Transición suave para hover */
}

.remove-button:hover {
  background-color: red;  /* Fondo rojo al pasar el mouse */
  color: white;  /* Texto blanco al pasar el mouse */
  border-color: darkred;  /* Cambiar el borde a rojo oscuro al hacer hover */
}

.remove-button:active {
  transform: scale(0.98);  /* Efecto de presionar el botón */
}
</style>
