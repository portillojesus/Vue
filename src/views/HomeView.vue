<template>
  <div class="home text-center py-5">
    <div class="container">
      <br>
      <h1 class="display-4 fw-bold text-primary">Bienvenido a la Aplicación de Tareas con Vue</h1>
      <p class="lead text-muted mb-5">
        Organiza tus tareas de manera eficiente y sencilla. ¡Empieza a gestionar ahora!
      </p>
      <br>
      <img alt="Vue logo" src="../assets/logo.png" class="logo mb-4" />
      <h1 class="display-4 fw-bold text-primary">Secciones de la Aplicacion</h1>
      <p>Añadir Tarea: Permite ingresar nuevas tareas manualmente.</p>
      <p>Lista de Tareas: Muestra todas las tareas extraídas desde la API, permitiendo marcarlas como completadas o eliminarlas.</p>
      <p>Vista Combinada: Combina las funcionalidades de añadir tareas manualmente y ver las tareas de la API al mismo tiempo.</p>
    </div>
  </div>
</template>

<style scoped>
.home {
  background-color: #f8f9fa;
}

.logo {
  width: 120px;
}

.display-4 {
  font-size: 2.8rem;
}

.h2{
  background-color: green;
}


</style>
