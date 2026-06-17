<template>
  <div class="card" @click="expandida = !expandida">

    <img :src="platillo.imagen" :alt="platillo.nombre" class="card-imagen" />

    <div class="card-cuerpo">
      <span class="card-categoria">{{ platillo.categoria }}</span>
      <h2 class="card-nombre">{{ platillo.nombre }}</h2>
      <p class="card-descripcion">{{ platillo.descripcion }}</p>

      <div v-if="expandida" class="card-extra" @click.stop>

        <div class="ingredientes">
          <h3>🧅 Ingredientes</h3>
          <ul>
            <li v-for="ing in platillo.ingredientes" :key="ing">{{ ing }}</li>
          </ul>
        </div>

        <div class="curiosidad">
          <h3>💡 ¿Sabías que...?</h3>
          <p>{{ platillo.curiosidad }}</p>
        </div>

        <div v-if="platillo.audio" class="audio-seccion">
          <h3>🔊 Narración</h3>
          <AudioPlayer :archivo="platillo.audio" />
        </div>

      </div>

      <button class="btn-expandir">
        {{ expandida ? '▲ Ver menos' : '▼ Ver más' }}
      </button>
    </div>

  </div>
</template>

<script setup>
import { ref } from 'vue'
import AudioPlayer from './AudioPlayer.vue'

defineProps({
  platillo: Object
})

const expandida = ref(false)
</script>

<style scoped>
.card {
  background: var(--fondo-card);
  border-radius: 12px;
  overflow: hidden;
  border: 1px solid var(--borde);
  cursor: pointer;
  transition: transform 0.2s, box-shadow 0.2s;
  display: flex;
  flex-direction: column;
}

.card:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 24px rgba(0,0,0,0.12);
}

.card-imagen {
  width: 100%;
  height: 200px;
  object-fit: cover;
}

.card-cuerpo {
  padding: 1.2rem;
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  flex: 1;
}

.card-categoria {
  display: inline-block;
  background: var(--primario);
  color: white;
  font-size: 0.75rem;
  font-weight: bold;
  padding: 0.2rem 0.7rem;
  border-radius: 20px;
  text-transform: uppercase;
  letter-spacing: 0.5px;
  width: fit-content;
}

.card-nombre {
  font-size: 1.3rem;
  color: var(--primario);
}

.card-descripcion {
  font-size: 0.9rem;
  color: var(--texto-suave);
  line-height: 1.5;
}

.card-extra {
  margin-top: 0.8rem;
  display: flex;
  flex-direction: column;
  gap: 1rem;
  border-top: 1px solid var(--borde);
  padding-top: 0.8rem;
}

.ingredientes h3,
.curiosidad h3,
.audio-seccion h3 {
  font-size: 0.95rem;
  margin-bottom: 0.4rem;
  color: var(--texto);
}

.ingredientes ul {
  list-style: none;
  display: flex;
  flex-wrap: wrap;
  gap: 0.4rem;
}

.ingredientes ul li {
  background: var(--fondo);
  border: 1px solid var(--borde);
  border-radius: 12px;
  padding: 0.2rem 0.6rem;
  font-size: 0.8rem;
  color: var(--texto-suave);
}

.curiosidad p {
  font-size: 0.88rem;
  color: var(--texto-suave);
  line-height: 1.5;
  font-style: italic;
}

.btn-expandir {
  margin-top: auto;
  padding-top: 0.8rem;
  background: none;
  border: none;
  color: var(--primario);
  font-size: 0.85rem;
  font-weight: bold;
  cursor: pointer;
  text-align: left;
}

.btn-expandir:hover {
  text-decoration: underline;
}
</style>