<template>
  <div class="schedule-wrapper">
    <h2 class="title">Mi horario semanal</h2>

    <ul class="days-list">
     <li v-for="(horas, dia) in horario" :key="dia">
  <span><strong>{{ dia }}:</strong></span>
  <span>{{ horas || '—' }}</span>
</li>
    </ul>

    <p class="total-hours">Total horas: <strong>{{ totalHoras }} h</strong></p>

    <button class="history-btn">Ver histórico</button>
  </div>
</template>

<script setup>
const horario = {
  Lunes: '09:00 - 13:00',
  Martes: '14:00 - 18:00',
  Miércoles: '09:00 - 13:00',
  Jueves: '',
  Viernes: '10:00 - 14:00'
}

const totalHoras = 16
</script>

<style scoped>
.schedule-wrapper {
  padding: 2rem 1.5rem;
  background: white;
  color: #333;
  border-radius: 16px;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.08);
  max-width: 340px;
  margin: 2rem auto;
  font-family: 'Inter', sans-serif;
  text-align: center;
}

.title {
  font-size: 1.4rem;
  font-weight: 600;
  margin-bottom: 1.5rem;
}

.days-list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.days-list li {
  display: flex;
  justify-content: space-between;
  padding: 0.5rem 0;
  border-bottom: 1px solid #e0e0e0;
  font-size: 1rem;
  font-weight: 500;
}

.total-hours {
  margin-top: 1rem;
  font-size: 0.95rem;
  color: #555;
}

.history-btn {
  margin-top: 1.5rem;
  width: 100%;
  padding: 0.75rem;
  background-color: #3b82f6;
  color: white;
  font-weight: 600;
  border: none;
  border-radius: 10px;
  cursor: pointer;
  transition: background 0.3s ease;
}

.history-btn:hover {
  background-color: #2563eb;
}

/* Modo oscuro */
[data-theme='dark'] .schedule-wrapper {
  background: #1e1e1e;
  color: #f0f0f0;
}

[data-theme='dark'] .days-list li {
  border-bottom: 1px solid #333;
}

[data-theme='dark'] .total-hours {
  color: #ccc;
}
[data-theme='dark'] .history-btn {
  background-color: #3b82f6;
  color: white;
}
