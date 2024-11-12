<template>
    <div class="container">
      <h1 class="text-center my-4">Vista Combinada</h1>
  
      <!-- Sección para añadir nueva tarea -->
      <div class="add-task-container mb-5">
        <h2 class="text-primary">Añadir Tarea</h2>
        <div class="input-group">
          <input 
            v-model="newTask" 
            @keyup.enter="addTask" 
            placeholder="Añadir nueva tarea" 
            class="form-control"
          />
          <button @click="addTask" class="btn btn-success ms-2">Añadir</button>
        </div>
      </div>
  
      <!-- Lista de tareas -->
      <div class="task-list-container">
        <h2 class="text-primary">Lista de Tareas</h2>
        <button @click="fetchTasks" class="btn btn-info mb-3">Cargar Tareas de Prueba</button>
        <div v-if="tasks.length > 0" class="list-group">
          <div v-for="task in tasks" :key="task.id" class="list-group-item d-flex justify-content-between align-items-center">
            <span :class="{ 'text-decoration-line-through text-muted': task.completed }" class="fw-bold">
              {{ task.todo }}
            </span>
            <div class="button-group d-flex">
              <button 
                @click="toggleTaskCompletion(task)" 
                class="btn btn-sm me-2" 
                :class="task.completed ? 'btn-primary' : 'btn-success'"
                style="width: 100px;"
              >
                {{ task.completed ? 'Desmarcar' : 'Completar' }}
              </button>
              <button 
                @click="deleteTask(task)" 
                class="btn btn-sm btn-danger" 
                style="width: 100px;"
              >
                Eliminar
              </button>
            </div>
          </div>
        </div>
        <p v-else class="text-muted">No hay tareas aún. ¡Añade una nueva tarea o carga tareas de prueba!</p>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: "CombinedView",
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
      async fetchTasks() {
        try {
          const response = await fetch("https://dummyjson.com/todos");
          const data = await response.json();
          this.tasks = data.todos;
        } catch (error) {
          console.error("Error al cargar las tareas:", error);
        }
      },
      toggleTaskCompletion(task) {
        task.completed = !task.completed;
      },
      deleteTask(task) {
        this.tasks = this.tasks.filter((t) => t.id !== task.id);
      },
    },
  };
  </script>
  
  <style scoped>
  .add-task-container {
    background-color: #f8f9fa;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  }
  
  .task-list-container {
    background-color: #ffffff;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  }
  
  .list-group-item {
    border: 1px solid #ddd;
    border-radius: 5px;
    margin-bottom: 10px;
    padding: 10px 15px;
  }
  
  .text-decoration-line-through {
    text-decoration: line-through;
  }
  
  .button-group {
    display: flex;
    gap: 5px;
  }
  </style>
  