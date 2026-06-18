# 🍛 Enciclopedia Gastronómica Costarricense

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

| Componente | Descripción |

| `NavBar.vue` | Barra de navegación con toggle de modo oscuro |
| `SearchBar.vue` | Buscador y botones de filtro por categoría |
| `EntradaCard.vue` | Tarjeta expandible de cada platillo |
| `AudioPlayer.vue` | Reproductor de audio con barra de progreso |

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


### Despliegue de información 


### Filtro


### Busqueda 



---

## Referencias

Ver [REFERENCIAS.md](./REFERENCIAS.md) para la lista completa de recursos consultados.