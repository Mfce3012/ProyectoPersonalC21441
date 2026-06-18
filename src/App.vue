<template>
  <div id="app" :class="{ 'modo-oscuro': modoOscuro }">

    <NavBar :modoOscuro="modoOscuro" @toggleModo="modoOscuro = !modoOscuro" />

    <main class="contenedor">
      <header class="encabezado">
        <h1 class="titulo-principal">🍛 Gastronomía Típica Costarricense</h1>
        <p class="subtitulo">Descubrí los sabores que definen nuestra identidad</p>
      </header>

      <SearchBar
        v-model:busqueda="busqueda"
        :categorias="categorias"
        :categoriaActiva="categoriaActiva"
        @cambiarCategoria="categoriaActiva = $event"
      />

      <p class="resultado-count">{{ platillosFiltrados.length }} platillos encontrados</p>

      <Transition name="fade" mode="out-in">
        <div v-if="platillosFiltrados.length > 0" :key="categoriaActiva + busqueda" class="grilla">
          <EntradaCard
            v-for="platillo in platillosFiltrados"
            :key="platillo.id"
            :platillo="platillo"
          />
        </div>
      </Transition>

      <p v-if="platillosFiltrados.length === 0" class="sin-resultados">
        No se encontraron platillos. Intentá con otro término. 🤷
      </p>

    </main>
  </div>
</template>

<script setup>
import { ref, computed, onMounted, watch } from 'vue'
import NavBar from './components/NavBar.vue'
import SearchBar from './components/SearchBar.vue'
import EntradaCard from './components/EntradaCard.vue'

const platillos       = ref([])
const busqueda        = ref('')
const categoriaActiva = ref('Todas')
const modoOscuro      = ref(false)

const categorias = ['Todas', 'Desayuno', 'Plato Fuerte', 'Antojito', 'Sopa', 'Postre', 'Bebida']

const platillosFiltrados = computed(() => {
  return platillos.value.filter(p => {
    const textoBusqueda = busqueda.value.toLowerCase()
    const coincideTexto =
      p.nombre.toLowerCase().includes(textoBusqueda) ||
      p.descripcion.toLowerCase().includes(textoBusqueda)
    const coincideCategoria =
      categoriaActiva.value === 'Todas' || p.categoria === categoriaActiva.value
    return coincideTexto && coincideCategoria
  })
})

onMounted(async () => {
  const res = await fetch('/data/platillos.json')
  platillos.value = await res.json()
})

watch(busqueda, (nuevoValor) => {
  if (nuevoValor.length > 0) {
    categoriaActiva.value = 'Todas'
  }
})
</script>

<style>
:root {
  --fondo:          #f5f0e8;
  --fondo-card:     #ffffff;
  --texto:          #2c1810;
  --texto-suave:    #6b4c3b;
  --primario:       #8B4513;
  --primario-hover: #6b340f;
  --borde:          #e0d5c8;
}

.modo-oscuro {
  --fondo:          #1a0e0a;
  --fondo-card:     #2a1810;
  --texto:          #f0e6d3;
  --texto-suave:    #c4956a;
  --primario:       #D2691E;
  --primario-hover: #e07825;
  --borde:          #3d2415;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

#app {
  min-height: 100vh;
  background: var(--fondo);
  color: var(--texto);
  transition: background 0.3s, color 0.3s;
}

.contenedor {
  max-width: 1200px;
  margin: 0 auto;
  padding: 2rem 1rem;
}

.encabezado {
  text-align: center;
  margin-bottom: 2rem;
}

.titulo-principal {
  font-size: 2.4rem;
  color: var(--primario);
  margin-bottom: 0.5rem;
}

.subtitulo {
  font-size: 1.1rem;
  color: var(--texto-suave);
}

.resultado-count {
  text-align: center;
  color: var(--texto-suave);
  font-size: 0.9rem;
  margin: 1rem 0;
}

.grilla {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 1.5rem;
}

.sin-resultados {
  text-align: center;
  font-size: 1.2rem;
  color: var(--texto-suave);
  margin-top: 3rem;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.25s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

@media (max-width: 600px) {
  .titulo-principal { font-size: 1.7rem; }
  .grilla { grid-template-columns: 1fr; }
}
</style>