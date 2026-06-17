<template>
  <div class="searchbar">

    <input
      class="input-busqueda"
      type="text"
      placeholder="🔍 Buscá un platillo..."
      :value="busqueda"
      @input="$emit('update:busqueda', $event.target.value)"
    />

    <div class="filtros">
      <button
        v-for="cat in categorias"
        :key="cat"
        class="btn-categoria"
        :class="{ activo: categoriaActiva === cat }"
        @click="$emit('cambiarCategoria', cat)"
      >
        {{ cat }}
      </button>
    </div>

  </div>
</template>

<script setup>
defineProps({
  busqueda:        String,
  categorias:      Array,
  categoriaActiva: String
})

defineEmits(['update:busqueda', 'cambiarCategoria'])
</script>

<style scoped>
.searchbar {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  margin-bottom: 1rem;
}

.input-busqueda {
  width: 100%;
  padding: 0.8rem 1.2rem;
  font-size: 1rem;
  border: 2px solid var(--borde);
  border-radius: 30px;
  background: var(--fondo-card);
  color: var(--texto);
  outline: none;
  transition: border-color 0.2s;
}

.input-busqueda:focus {
  border-color: var(--primario);
}

.filtros {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  justify-content: center;
}

.btn-categoria {
  padding: 0.4rem 1rem;
  border-radius: 20px;
  border: 2px solid var(--borde);
  background: var(--fondo-card);
  color: var(--texto);
  cursor: pointer;
  font-size: 0.85rem;
  transition: all 0.2s;
}

.btn-categoria:hover {
  border-color: var(--primario);
  color: var(--primario);
}

.btn-categoria.activo {
  background: var(--primario);
  border-color: var(--primario);
  color: white;
  font-weight: bold;
}
</style>