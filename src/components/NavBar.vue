<template>
    <nav class="navbar">
        <div class="navbar-menu">
            <ul class="nav-list">
                <li v-for="nav in navegacion" :key="nav.nombre" class="nav-item">
                    <a :href="nav.enlace" class="nav-link">{{nav.nombre}}</a>
                </li>
            </ul>
        </div>
    </nav>
</template>

<script setup>
import { ref } from 'vue';
const navegacion = ref([
    { id: 1, nombre: 'Educación', enlace: '#educacion' },
    { id: 2, nombre: 'Experiencia', enlace: '#experiencia' },
    { id: 3, nombre: 'Proyectos', enlace: '#proyectos' },
    { id: 4, nombre: 'Habilidades', enlace: '#habilidades' },
    { id: 5, nombre: 'Intereses', enlace: '#intereses' }
]);
</script>

<style scoped>
.navbar {
    background-color: #815a72;
    border-radius: 20px;
    color: #fff;
    padding: 0.5rem 1rem;
    align-items: center;
}

.navbar-menu {
    display: flex;
    justify-content: center;
    width: 100%;
}

.nav-list {
    display: flex;
    justify-content: space-around; /* Distribuye los elementos a lo largo de la barra */
    width: 100%;
    padding: 0;
    margin: 0;
    list-style: none;
}

.nav-item {
    display: flex;
}

.nav-link {
    color: #b0a8b9;
    border: solid 1px #b0a8b9;
    border-radius: 20px;
    padding: 5px 15px; /* Ajusta el tamaño del padding para botones más pequeños */
    text-decoration: none;
    text-align: center;
}

.nav-link:hover {
    color: #815a72;
    background-color: #d3cadc;
    border-color: #815a72;
}

@media (max-width: 768px) {
  .navbar-menu {
    justify-content: space-around;
    width: 100%;
  }
}
</style>
