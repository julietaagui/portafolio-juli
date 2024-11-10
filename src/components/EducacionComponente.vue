<script setup>
import { ref } from 'vue';
const fechaColor = ref([]);

fechaColor.value = [
  {color: '#d9a5db'},
  {color: '#ff8b5c'},
  {color: '#a87561'},
  {color: '#fd8a7d'},
  {color: '#78aaa2'}
];

const educacion = ref([
  {fecha: 'Enero', title: 'Curso de HTML, CSS, JavaScript, MySQL, PHP.', descripcion: 'La enseñanza fue acompañada de muchos proyectos dinamicos. Entre ellos hice un proyecto de ventas de bienes raices.', enlace:'https://profound-biscochitos-560214.netlify.app/'},
  {fecha: 'Mayo', title: 'Curso Front-End', descripcion: 'En ente curso afirme mis conocimientos en JavaScript, HTML y CSS con un proyecto de cursos de cafeteria.', enlace:'https://rainbow-gumdrop-068613.netlify.app/'},
  {fecha: 'Agosto', title: 'Curso de React y JavaScript', descripcion: 'En este curso aprendi a hacer funcionar un carrito de compras con un proyecto Ecommerce de guitarras', enlace:'https://amazing-cranachan-8b5f0c.netlify.app/'},
  {fecha: 'Noviembre', title: 'Curso de JavaScript Moderno', descripcion: 'En este curso aprendi a programar dinamicamente. Con este curso hice un proyecto para cotizar vehiculos.', enlace:'https://fabulous-kataifi-10f47b.netlify.app/'},
  {fecha: 'Diciembre', title: 'Graduacion como Tecnica Universitaria en Programacion', descripcion: 'Los lenguajes que aprendi en estos dos ños de carrera fueron: Python, Java Y JavaScript, para el frontend aprendimos HTML y CSS, para el manejo de base de datos aprendimos MySQL y MongoDB', enlace:'https://github.com/CodeStrong2023/CodeMasters_4_semestre'}
]);
</script>

<template>
    <ul>
        <li v-for="(item, index) in educacion" :key="index" :style="{ '--fecha-color': fechaColor[index].color}">
        <div class="fecha">{{ item.fecha }}</div>
        <h3 class="title">{{ item.title }}</h3>
        <div class="descripcion">{{ item.descripcion }}</div>
        <a class="enlace" :href="item.enlace" target="_blank">Saber más</a>
    </li>
    </ul>
</template>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300;500;700&display=swap");
*,
*::before,
*::after {
  margin: 0; 
  padding: 0; 
  box-sizing: border-box; 
}

body {
  --color: rgba(30, 30, 30); 
  --bgColor: rgba(245, 245, 245); 
  min-height: 100vh; 
  display: grid; 
  align-content: center; 
  gap: 2rem;
  padding: 2rem; 
  font-family: "Poppins", sans-serif; 
  color: var(--color); 
  background: var(--bgColor); 
}

ul {
    margin-top: 2rem;
  --col-gap: 2rem; 
  --row-gap: 2rem; 
  --line-w: 0.25rem;
  display: grid; 
  grid-template-columns: var(--line-w) 1fr; 
  grid-auto-columns: max-content; 
  column-gap: var(--col-gap); 
  list-style: none; 
  width: min(60rem, 90%); 
  margin-inline: auto; 
}

ul::before {
  content: ""; 
  grid-column: 1; 
  grid-row: 1 / span 20; 
  background: rgb(225, 225, 225); 
  border-radius: calc(var(--line-w) / 2); 
}

ul li:not(:last-child) {
  margin-bottom: var(--row-gap); 
}

ul li {
  grid-column: 2; 
  --inlineP: 1.5rem; 
  margin-inline: var(--inlineP); 
  grid-row: span 2; 
  display: grid; 
  grid-template-rows: min-content min-content min-content; 
}

ul li .fecha {
  --dateH: 3rem; /* Altura de la sección de la fecha */
  height: var(--dateH); /* Aplica la altura definida */
  margin-inline: calc(var(--inlineP) * -1); /* Ajusta el margen horizontal para que la fecha sobresalga */
  text-align: center; /* Centra el texto dentro de la fecha */
  background-color: var(--fecha-color); /* Color de fondo, usando una variable personalizada */
  color: white; /* Color del texto en la fecha */
  font-size: 1.25rem; /* Tamaño del texto */
  font-weight: 700; /* Hace el texto en negrita */
  display: grid; /* Usa un layout de cuadrícula */
  place-content: center; /* Centra el contenido de la fecha */
  position: relative; /* Posiciona la fecha relativa a su contenedor */
  border-radius: calc(var(--dateH) / 2) 0 0 calc(var(--dateH) / 2); /* Bordes redondeados para la fecha */
}

/* Estilo para la parte inferior de la fecha, que parece un triángulo */
ul li .fecha::before {
  content: ""; /* Elemento vacío para crear el triángulo */
  width: var(--inlineP); /* Ancho igual al espacio interno definido */
  aspect-ratio: 1; /* Mantiene una relación de aspecto 1:1 para crear un cuadrado */
  background: var(--fecha-color); /* Usa el color de fondo de la fecha */
  background-image: linear-gradient(rgba(0, 0, 0, 0.2) 100%, transparent); /* Aplica un degradado sutil para dar un efecto de sombra */
  position: absolute; /* Posiciona el triángulo respecto al contenedor de la fecha */
  top: 100%; /* Coloca el triángulo justo debajo de la fecha */
  clip-path: polygon(0 0, 100% 0, 0 100%); /* Recorta el cuadrado para convertirlo en un triángulo */
  right: 0; /* Alinea el triángulo a la derecha de la fecha */
}

/* Estilo para el círculo que conecta la fecha con la línea */
ul li .fecha::after {
  content: ""; /* Elemento vacío para crear el círculo */
  position: absolute; /* Posiciona el círculo respecto al contenedor de la fecha */
  width: 1rem; /* Ancho del círculo */
  aspect-ratio: 1; /* Mantiene una relación de aspecto 1:1 para crear un círculo */
  background: var(--bgColor); /* Color de fondo, utilizando la variable definida */
  border: 0.3rem solid var(--fecha-color); /* Borde del círculo, con el color de la fecha */
  border-radius: 50%; /* Hace que el elemento sea un círculo perfecto */
  top: 50%; /* Centra verticalmente el círculo dentro del contenedor de la fecha */
  transform: translate(50%, -50%); /* Ajusta la posición del círculo para alinearlo correctamente */
  right: calc(100% + var(--col-gap) + var(--line-w) / 2); /* Coloca el círculo a la izquierda de la línea */
}

/* Estilos para el título y la descripción dentro de cada ítem */
ul li .title,
ul li .descripcion {
  background: var(--bgColor); /* Fondo del título y la descripción, usando la variable definida */
  position: relative; /* Posiciona los elementos relativos a su contenedor */
  padding-inline: 1.5rem; /* Espaciado interno horizontal */
}

ul li .title {
  overflow: hidden; /* Oculta cualquier contenido que se desborde */
  padding-block-start: 1.5rem; /* Espaciado interno superior */
  padding-block-end: 1rem; /* Espaciado interno inferior */
  font-weight: 500; /* Hace el texto del título un poco más grueso */
}

ul li .descripcion {
  padding-block-end: 1.5rem; /* Espaciado interno inferior */
  font-weight: 300; /* Hace el texto de la descripción más delgado */
}

/* Estilos para las sombras debajo del título y la descripción */
ul li .title::before,
ul li .descripcion::before {
  content: ""; /* Elemento vacío para crear la sombra */
  position: absolute; /* Posiciona la sombra respecto al contenedor del título o descripción */
  width: 90%; /* Ancho de la sombra */
  height: 0.5rem; /* Altura de la sombra */
  background: rgba(0, 0, 0, 0.5); /* Color de fondo oscuro para simular una sombra */
  left: 50%; /* Centra la sombra horizontalmente */
  border-radius: 50%; /* Bordes redondeados para la sombra */
  filter: blur(4px); /* Aplica un desenfoque para hacer la sombra más suave */
  transform: translate(-50%, 50%); /* Ajusta la posición para centrar la sombra */
}

ul li .title::before {
  bottom: calc(100% + 0.125rem); /* Coloca la sombra debajo del título */
}

ul li .descripcion::before {
  z-index: -1; /* Coloca la sombra detrás del contenido */
  bottom: 0.25rem; /* Coloca la sombra justo*/
}


/* Media query para pantallas anchas (40rem o más) */
@media (min-width: 40rem) {
  ul {
    grid-template-columns: 1fr var(--line-w) 1fr; /* Ajusta la cuadrícula para tener tres columnas */
  }
  ul::before {
    grid-column: 2; /* Mueve la línea vertical a la segunda columna de la cuadrícula */
  }
  ul li:nth-child(odd) {
    grid-column: 1; /* Coloca los ítems impares en la primera columna */
  }
  ul li:nth-child(even) {
    grid-column: 3; /* Coloca los ítems pares en la tercera columna */
  }

  /* Ajuste para que el segundo ítem abarque dos filas */
  ul li:nth-child(2) {
    grid-row: 2/4; /* El segundo ítem ocupará desde la segunda hasta la cuarta fila */
  }

  /* Ajustes específicos para los ítems impares */
  ul li:nth-child(odd) .fecha::before {
    clip-path: polygon(0 0, 100% 0, 100% 100%); /* Invierte el triángulo en los ítems impares */
    left: 0; /* Alinea el triángulo a la izquierda */
  }

  ul li:nth-child(odd) .fecha::after {
    transform: translate(-50%, -50%); /* Ajusta la posición del círculo en los ítems impares */
    left: calc(100% + var(--col-gap) + var(--line-w) / 2); /* Coloca el círculo a la derecha de la línea */
  }

  ul li:nth-child(odd) .fecha {
    border-radius: 0 calc(var(--dateH) / 2) calc(var(--dateH) / 2) 0; /* Ajusta los bordes redondeados para los ítems impares */
  }
}

/* Estilo para los créditos */
.credits {
  margin-top: 1rem; /* Espaciado superior para los créditos */
  text-align: right; /* Alinea el texto de los créditos a la derecha */
}
.credits a {
  color: var(--color); /* Aplica el color de texto definido en la variable */
}
</style>