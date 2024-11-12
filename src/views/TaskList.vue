<template>
    <div class="task-list-container d-flex justify-content-center">
      <div class="task-list-wrapper">
        <h1 class="text-primary text-center mb-4">Lista de Tareas</h1>
        <button class="btn btn-info mb-3" @click="fetchTasks">
          Cargar Tareas
        </button>
        <div v-if="tasks.length > 0">
          <div
            v-for="task in tasks"
            :key="task.id"
            class="task-item p-3 mb-3 shadow-sm rounded d-flex justify-content-between align-items-center"
          >
            <div>
              <h5 :class="{ 'text-decoration-line-through': task.completed }">
                {{ task.todo }}
              </h5>
              <span
                class="badge"
                :class="task.completed ? 'bg-success' : 'bg-warning'"
              >
                {{ task.completed ? 'Completada' : 'Pendiente' }}
              </span>
            </div>
            <div class="button-group d-flex gap-2">
              <button
                class="btn btn-success btn-sm"
                @click="toggleTaskCompletion(task)"
              >
                Completar
              </button>
              <button
                class="btn btn-danger btn-sm"
                @click="deleteTask(task)"
              >
                Eliminar
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: "TaskList",
    data() {
      return {
        tasks: [],
      };
    },
    methods: {
      fetchTasks() {
        fetch("https://dummyjson.com/todos")
          .then((response) => response.json())
          .then((data) => {
            this.tasks = data.todos;
          });
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
  .task-list-container {
    min-height: 100vh;
    padding: 20px;
    margin-top: 50px;
  }
  
  .task-list-wrapper {
    width: 100%;
    max-width: 600px;
  }
  
  .task-item {
    background-color: #ffffff;
  }
  
  .text-decoration-line-through {
    text-decoration: line-through;
  }
  
  .button-group {
    display: flex;
    justify-content: flex-end;
    gap: 10px;
  }
  </style>
  