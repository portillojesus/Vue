<template>
    <div class="container">
      <h1 class="text-center text-success my-4">Añadir Tarea</h1>
      <div class="input-group mb-3">
        <input 
          type="text" 
          v-model="newTask" 
          @keyup.enter="addTask" 
          class="form-control" 
          placeholder="Añadir nueva tarea"
        />
        <button @click="addTask" class="btn btn-primary">Añadir</button>
      </div>
  
      <div v-if="tasks.length > 0" class="task-list mt-4">
        <div 
          v-for="task in tasks" 
          :key="task.id" 
          class="task-item border rounded p-3 d-flex justify-content-between align-items-center mb-2"
        >
          <span :class="{ 'text-decoration-line-through text-muted': task.completed }">
            {{ task.todo }}
          </span>
          <div>
            <button 
              @click="toggleTaskCompletion(task)" 
              class="btn btn-sm me-2" 
              :class="task.completed ? 'btn-secondary' : 'btn-success'"
            >
              {{ task.completed ? 'Desmarcar' : 'Completar' }}
            </button>
            <button @click="deleteTask(task)" class="btn btn-sm btn-danger">Eliminar</button>
          </div>
        </div>
      </div>
      <p v-else class="text-muted mt-4">No hay tareas aún. ¡Añade una nueva tarea!</p>
    </div>
  </template>
  
  <script>
  export default {
    name: "AddTask",
    data() {
      return {
        newTask: "",
        tasks: [],
      };
    },
    methods: {
      addTask() {
        if (this.newTask.trim() === "") return;
        const newTask = {
          todo: this.newTask,
          completed: false,
          id: Date.now(),
        };
        this.tasks.unshift(newTask);
        this.newTask = "";
      },
      deleteTask(task) {
        this.tasks = this.tasks.filter((t) => t.id !== task.id);
      },
      toggleTaskCompletion(task) {
        task.completed = !task.completed;
      },
    },
  };
  </script>
  
  <style scoped>
  .task-item {
    background-color: #f8f9fa;
  }
  </style>
  