<template>
  <nav class="navbar">
    <div class="navbar-contenido">

      <div class="navbar-marca">
        <span class="navbar-icono"></span>
        <span class="navbar-titulo">Gastro CR</span>
      </div>

      <button class="btn-modo" @click="$emit('toggleModo')" :title="modoOscuro ? 'Modo claro' : 'Modo oscuro'">
        {{ modoOscuro ? '☀️ Modo claro' : '🌙 Modo oscuro' }}
      </button>

    </div>
  </nav>
</template>

<script setup>
defineProps({
  modoOscuro: Boolean
})

defineEmits(['toggleModo'])
</script>

<style scoped>
.navbar {
  background: var(--primario);
  padding: 1rem;
  box-shadow: 0 2px 8px rgba(0,0,0,0.2);
  position: sticky;
  top: 0;
  z-index: 100;
}

.navbar-contenido {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.navbar-marca {
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.navbar-icono {
  font-size: 1.5rem;
}

.navbar-titulo {
  font-size: 1.4rem;
  font-weight: bold;
  color: white;
  letter-spacing: 1px;
}

.btn-modo {
  background: rgba(255,255,255,0.2);
  border: 2px solid rgba(255,255,255,0.4);
  color: white;
  padding: 0.4rem 1rem;
  border-radius: 20px;
  cursor: pointer;
  font-size: 0.9rem;
  transition: background 0.2s;
}

.btn-modo:hover {
  background: rgba(255,255,255,0.35);
}
</style>