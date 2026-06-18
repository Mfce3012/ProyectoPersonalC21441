# Enciclopedia Gastronómica Costarricense

Aplicación web multimedia desarrollada como proyecto personal del curso **IF7102 Multimedios**, I Ciclo 2026, Universidad de Costa Rica — Sede de Guanacaste.

**Estudiante:** María Félix Cabezas Espinoza
**Carné:** C21441  
**Framework:** Vue 3 con Vite  
**Opción:** Opción 4 — Enciclopedia Temática Interactiva

---

## Descripción

Enciclopedia interactiva con 12 platillos típicos de la gastronomía costarricense. Permite explorar, buscar y filtrar entradas por categoría, con información detallada, ingredientes, curiosidades y narración en audio para tres platillos.

---

## Funcionalidades

- Búsqueda en tiempo real por nombre o descripción
- Filtros por categoría (Desayuno, Plato Fuerte, Antojito, Sopa, Postre, Bebida)
- Modo oscuro / modo claro
- Reproductor de audio integrado en 3 entradas
- Diseño responsivo para escritorio y móvil
- Transiciones animadas al filtrar

---

## Componentes Vue
`NavBar.vue` | Barra de navegación con toggle de modo oscuro
`SearchBar.vue` | Buscador y botones de filtro por categoría 
`EntradaCard.vue` | Tarjeta expandible de cada platillo 
`AudioPlayer.vue` | Reproductor de audio con barra de progreso 

---

## Características técnicas de Vue 3

- `ref` y `computed` para reactividad
- `onMounted` para carga de datos con `fetch()`
- `watch` para sincronizar búsqueda y categoría
- `defineProps` y `defineEmits` en todos los componentes
- `v-for`, `v-if`, `v-model` y `:class` bindings
- `<Transition>` para animaciones de filtrado
- CSS variables para theming de modo oscuro

---

## Cómo ejecutar el proyecto

```bash
npm install
npm run dev
```

Luego abrí http://localhost:5173 en el navegador.

---

## Estructura del proyecto

```
src/
├── components/
│   ├── NavBar.vue
│   ├── SearchBar.vue
│   ├── EntradaCard.vue
│   └── AudioPlayer.vue
├── App.vue
└── main.js

public/
├── data/
│   └── platillos.json
├── images/
│   └── (12 imágenes de platillos)
└── audio/
    └── (3 archivos de narración)
```

---

## Capturas de pantalla
 ### Sitio completo 
<img width="1918" height="1026" alt="imagen" src="https://github.com/user-attachments/assets/54b113ff-ceaa-42e7-a9c7-af333236b002" />

### Despliegue de información 
<img width="558" height="952" alt="imagen" src="https://github.com/user-attachments/assets/e49fe01a-db5e-4df5-92c4-2307b4528047" />

### Filtro
<img width="1368" height="933" alt="imagen" src="https://github.com/user-attachments/assets/4131d3c9-24c5-4992-9877-b2f6cfa55037" />

### Busqueda 
<img width="1546" height="835" alt="imagen" src="https://github.com/user-attachments/assets/687825e9-9b56-4185-8f11-0d693f04f427" />

---

## Referencias

Ver [REFERENCIAS.md](./REFERENCIAS.md) para la lista completa de recursos consultados.
