<template>
  <div class="audio-player">
    <audio ref="audioRef" :src="`/audio/${archivo}`" @timeupdate="actualizarTiempo" @ended="reproduciendo = false"></audio>

    <button class="btn-play" @click="togglePlay">
      {{ reproduciendo ? '⏸ Pausar' : '▶ Reproducir' }}
    </button>

    <div class="barra-contenedor">
      <div class="barra-progreso">
        <div class="barra-relleno" :style="{ width: progreso + '%' }"></div>
      </div>
      <span class="tiempo">{{ tiempoActual }}</span>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

defineProps({
  archivo: String
})

const audioRef    = ref(null)
const reproduciendo = ref(false)
const progreso    = ref(0)
const tiempoActual = ref('0:00')

function togglePlay() {
  if (reproduciendo.value) {
    audioRef.value.pause()
  } else {
    audioRef.value.play()
  }
  reproduciendo.value = !reproduciendo.value
}

function actualizarTiempo() {
  const audio = audioRef.value
  progreso.value = (audio.currentTime / audio.duration) * 100
  const seg = Math.floor(audio.currentTime)
  tiempoActual.value = `${Math.floor(seg / 60)}:${String(seg % 60).padStart(2, '0')}`
}
</script>

<style scoped>
.audio-player {
  display: flex;
  align-items: center;
  gap: 0.8rem;
  background: var(--fondo);
  border: 1px solid var(--borde);
  border-radius: 8px;
  padding: 0.6rem 1rem;
}

.btn-play {
  background: var(--primario);
  color: white;
  border: none;
  border-radius: 6px;
  padding: 0.3rem 0.8rem;
  cursor: pointer;
  font-size: 0.85rem;
  white-space: nowrap;
}

.btn-play:hover {
  background: var(--primario-hover);
}

.barra-contenedor {
  flex: 1;
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.barra-progreso {
  flex: 1;
  height: 6px;
  background: var(--borde);
  border-radius: 3px;
  overflow: hidden;
}

.barra-relleno {
  height: 100%;
  background: var(--primario);
  border-radius: 3px;
  transition: width 0.3s;
}

.tiempo {
  font-size: 0.8rem;
  color: var(--texto-suave);
  min-width: 30px;
}
</style>