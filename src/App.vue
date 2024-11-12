<template>
  <div id="app">
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark shadow">
      <div class="container">
        <router-link class="navbar-brand fw-bold" to="/">
          <i class="bi bi-clipboard-check"></i> Gestor de Tareas
        </router-link>
        <button
          class="navbar-toggler"
          type="button"
          data-bs-toggle="collapse"
          data-bs-target="#navbarNav"
          aria-controls="navbarNav"
          aria-expanded="false"
          aria-label="Toggle navigation"
        >
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarNav">
          <ul class="navbar-nav ms-auto">
            <li class="nav-item">
              <router-link class="nav-link" to="/addtask">Añadir Tarea</router-link>
            </li>
            <li class="nav-item">
              <router-link class="nav-link" to="/tasklist">Lista de Tareas</router-link>
            </li>
            <li class="nav-item">
              <router-link class="nav-link" to="/combinedview">Vista Combinada</router-link>
            </li>
          </ul>
        </div>
      </div>
    </nav>
    <router-view/>
  </div>
</template>

<style>
#app {
  font-family: 'Poppins', sans-serif;
}

.navbar {
  background-color: #1c1f26;
}

.nav-link {
  font-size: 1.1rem;
  padding: 10px;
}

.nav-link.active {
  color: #42b983 !important;
  font-weight: bold;
}
</style>

<link
  href="https://cdnjs.cloudflare.com/ajax/libs/bootstrap-icons/1.10.5/font/bootstrap-icons.min.css"
  rel="stylesheet"
/>
