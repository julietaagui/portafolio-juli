<script setup>
import proyecto1 from '/src/assets/cotizacion.png';
import proyecto2 from '/src/assets/cursos.png';
import proyecto3 from '/src/assets/guitar.png';
import proyecto4 from '/src/assets/mails.png';

// Este componente muestra una galería de proyectos con información sobre cada proyecto
import { ref } from 'vue';
//.ref es una función que se utiliza para crear una referencia reactiva en Vue 3
var misProyectos = ref([]);
//.value es una propiedad que se utiliza para acceder al valor de una referencia reactiva en Vue 3
misProyectos.value = ([
    //esto es un array de objetos que contiene información sobre los proyectos
    {
        id: 1,
        src: proyecto1,
        titulo: "Aplicación web Cotizador de Seguros de Vehiculos",
        descripcion: "Creé una aplicación web para enviar email con verificacion de sintaxis del gmail y con verificacion de campos obligatorios.",
        projectoLink: "https://fabulous-kataifi-10f47b.netlify.app/",
        githubLink: "https://github.com/julietaagui/cotizar-seguro"
    },
    {
        id: 2,
        src: proyecto2,
        titulo: "Aplicación web Ecommerce Cursos",
        descripcion: "Este proyecto fue diseñado con JavaScript, HTML y CSS para vender cursos.",
        projectoLink: "https://nimble-dasik-eb81fe.netlify.app/",
        githubLink: "https://github.com/julietaagui/ecommerce-cursos"
    },
    {
        id: 3,
        src: proyecto3,
        titulo: "Aplicación web Ecommerce GuitarLa",
        descripcion: "Construí un blog personal con un sistema de gestión de contenidos (CMS) personalizado en WordPress.",
        projectoLink: "https://amazing-cranachan-8b5f0c.netlify.app/",
        githubLink: "https://github.com/julietaagui/GuitarLA"
    },
    {
        id: 4,
        src: proyecto4,
        titulo: "Aplicación web para Enviar Emails",
        descripcion: "Creé una aplicación móvil con Flutter que permite a los usuarios reservar mesas en restaurantes locales",
        projectoLink: "https://sunny-yeot-1cbf64.netlify.app/",
        githubLink: "https://github.com/julietaagui/Enviar-Emails"
    },
])

</script>

<template>
    <!-- Aquí va el código HTML de la galería de proyectos -->
    <div class="galeria">
        <!-- Itera sobre cada proyecto en la lista de misProyectos -->
        <!--key es una propiedad especial que se utiliza para identificar de forma única cada elemento en una lista de Vue.js-->
        <li class="proyecto" v-for="proyecto in misProyectos" :key="proyecto.id">
            <!-- Muestra la imagen del proyecto utilizando : que es una directiva de enlace de atributo en Vue.js -->
            <img :src="proyecto.src" :alt="proyecto.titlulo">
            <div class="proyecto-info">
                <!-- Muestra el título y la descripción del proyecto utilizando la interpolación de Vue.js -->
                <h3>{{ proyecto.titulo }}</h3>
                <p>{{ proyecto.descripcion }}</p>
                <div class="proyecto-links">
                    <a :href="proyecto.projectoLink" class="btn-ver-mas " target="_blank" rel="noopener noreferrer">Ver
                        Proyecto</a>
                    <a :href="proyecto.githubLink" class="github-link" target="_blank" rel="noopener noreferrer">Ver
                        Código en GitHub</a>
                </div>
            </div>
        </li>
    </div>
</template>

<style scoped>
/*Estilo de fondo de la galeria con un fondo estatico */
/* .galeria {
    width: 100%;
    height: 100vh;
    display: flex;
    flex-wrap: wrap;
    gap: 20px;
    justify-content: center;
    background-image: url('/src/assets/fondo-proyectos.jpg');
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
} */

/* Estilos Fondo Animado de Css de la galería */
/* La clase 'galeria' es el contenedor principal de la galería de proyectos */
.galeria {
    /* Establece el ancho de la galería al 100% del contenedor padre */
    width: 100%;
    /* Establece la altura de la galería al 100% del contenedor padre */
    height: 100%;
    /* Utiliza flexbox para organizar los elementos hijos en la galería */
    display: flex;
    /* Permite que los elementos se ajusten y pasen a la siguiente línea si no caben en una sola fila */
    flex-wrap: wrap;
    /* Establece un espacio de 20px entre los elementos de la galería */
    gap: 20px;
    /* Agrega un padding de 20px alrededor de la galería */
    padding: 20px;
    /* Centra los elementos hijos horizontalmente */
    justify-content: center;
    /* Aplica un fondo con un degradado de colores */
    background: rgb(148,187,233);
    background: radial-gradient(circle, rgba(148,187,233,1) 22%, rgba(238,174,202,1) 84%);
    background-size: 400% 400%;
    animation: gradient 15s ease infinite;
}

/* Define una animación llamada 'gradient' para cambiar la posición del fondo */
@keyframes gradient {

    /* Al inicio, el fondo está posicionado en el 0% horizontal y 50% vertical */
    0% {
        background-position: 0% 50%;
    }

    /* A la mitad de la animación, el fondo se desplaza al 100% horizontal y 50% vertical */
    50% {
        background-position: 100% 50%;
    }

    /* Al final, el fondo vuelve a la posición inicial */
    100% {
        background-position: 0% 50%;
    }
}

/* La clase 'proyecto' es el contenedor individual de cada proyecto */
.proyecto {
    /* Utiliza flexbox para organizar el contenido del proyecto en una columna */
    display: flex;
    /* Establece la dirección de los elementos en columna */
    flex-direction: column;
    /* Aplica un borde de 2px sólido y color gris claro (#ddd) alrededor del proyecto */
    border: 1px solid #dfe0df;
    /* Redondea las esquinas del contenedor */
    border-radius: 8px;
    /* Oculta cualquier contenido que se desborde del contenedor */
    overflow: hidden;
    /* Establece un color de fondo claro para el proyecto */
    background-color: #f9f9f9;
    /* Define el ancho máximo del proyecto en 222px */
    max-width: 222px;
    /* Hace que el contenedor se ajuste flexiblemente ocupando al menos 300px de ancho */
    flex: 1 1 300px;
}

/* Estilo para las imágenes dentro del contenedor 'proyecto' */
.proyecto img {
    /* Hace que la imagen ocupe el 100% del ancho del contenedor */
    width: 100%;
    /* Mantiene la relación de aspecto de la imagen */
    height: auto;
    /* Asegura que la imagen se muestre como un bloque, sin espacio en línea alrededor */
    display: block;
}

/* La clase 'proyecto-info' contiene la información del proyecto */
.proyecto-info {
    /* Agrega un padding de 15px alrededor de la información */
    padding: 15px;
    /* Centra el texto dentro del contenedor */
    text-align: center;
}

/* Estilo para los títulos de los proyectos */
.proyecto-info h3 {
    /* Establece un margen superior e inferior de 10px */
    margin: 10px 0;
    /* Define el tamaño de la fuente a 1.3em (relativo al tamaño de fuente del contenedor) */
    font-size: 1.3em;
    /* Aplica un color gris oscuro (#333) al texto */
    color: #333;
}

/* Estilo para los párrafos de los proyectos */
.proyecto-info p {
    /* Establece un margen superior e inferior de 10px */
    margin: 10px 0;
    /* Define el tamaño de la fuente a 1em (igual al tamaño de fuente base) */
    font-size: 1em;
    /* Aplica un color gris (#666) al texto */
    color: #666;
}

/* La clase 'proyecto-links' organiza los enlaces y botones del proyecto */
.proyecto-links {
    /* Utiliza flexbox para organizar los enlaces en una columna */
    display: flex;
    /* Establece la dirección de los elementos en columna */
    flex-direction: column;
    /* Establece un espacio de 10px entre los elementos */
    gap: 10px;
    /* Agrega un margen superior de 10px */
    margin-top: 30px;

}

/* Estilo para el botón 'Ver Más' dentro de la clase 'proyecto-links' */
.proyecto-links .btn-ver-mas {
    /* Aplica un color de fondo azul (#007BFF) */
    background-color: #815a72;
    /* Aplica un color de texto blanco */
    color: #fff;
    /* Agrega un padding de 10px en vertical y 15px en horizontal */
    padding: 10px 15px;
    /* Redondea las esquinas del botón */
    border-radius: 5px;
    /* Elimina el subrayado del texto */
    text-decoration: none;
    /* Aplica una transición suave al cambiar el color de fondo */
    transition: background-color 0.3s;
    margin-top: 1rem;
}

/* Estilo para cuando el botón 'Ver Más' es hover */
.proyecto-links .btn-ver-mas:hover {
    /* Cambia el color de fondo a un azul más oscuro (#0056b3) */
    background-color: #f0dfd9;
    color: #333;
}

/* Estilo para el enlace a GitHub dentro de la clase 'proyecto-links' */
.proyecto-links .github-link {
    /* Aplica un color gris oscuro (#333) al texto */
    color: #333;
    /* Elimina el subrayado del texto */
    text-decoration: none;
    /* Establece el tamaño de fuente a 0.9em (un poco más pequeño que el tamaño base) */
    font-size: 0.9em;
}

/* Estilo para cuando el enlace a GitHub es hover */
.proyecto-links .github-link:hover {
    /* Añade un subrayado al texto */
    text-decoration: underline;
}
</style>