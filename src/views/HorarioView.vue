<template>
  <div class="horario-page">
    <h1>Mi horario semanal</h1>
    <ul class="horario-lista">
      <li v-for="(franja, dia) in horario" :key="dia">
        <strong>{{ dia }}:</strong> {{ franja }}
      </li>
    </ul>
    <p>Total horas: {{ totalHoras }} h</p>
    <button @click="verHistorico">Ver histórico</button>
  </div>
</template>

<script setup>
const horario = {
  Lunes: '09:00 - 13:00',
  Martes: '14:00 - 18:00',
  Miércoles: '09:00 - 13:00',
  Jueves: '—',
  Viernes: '10:00 - 14:00'
}

const totalHoras = 16

function verHistorico() {
  alert('Funcionalidad de histórico en desarrollo')
}
</script>

<style scoped>
.horario-page {
  max-width: 500px;
  margin: auto;
  padding: 2rem;
}
.horario-lista {
  list-style: none;
  padding: 0;
}
.horario-lista li {
  margin-bottom: 0.5rem;
}
</style>
