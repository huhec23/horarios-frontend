<template>
  <div class="login-wrapper">
    <p class="welcome-text">Gestión de turnos fácil y rápida</p>
    <img class="logo" :src="logoSrc" alt="Logo MiHorario" />

    <button class="toggle-theme" @click="toggleTheme">
      {{ darkMode ? 'MODO CLARO' : 'MODO OSCURO' }}
    </button>

    <form class="login-form" @submit.prevent="handleLogin">
      <h2>Bienvenido</h2>
      <p class="subtitle">Accede con tus credenciales</p>
      <input v-model="email" type="email" placeholder="Correo" required />
      <input v-model="password" type="password" placeholder="Contraseña" required />
      <button type="submit">Entrar</button>
      <a class="link-help" href="#">¿Has olvidado tu contraseña?</a>
    </form>

    <p class="footer">v1.0 · © 2025 MiHorario</p>
  </div>
</template>

<script setup>
import { ref, onMounted, computed } from 'vue'
import { useRouter } from 'vue-router'

const email = ref('')
const password = ref('')
const router = useRouter()

function handleLogin() {
  if (email.value && password.value) {
    router.push('/horario')
  }
}

// 🌙 Modo claro/oscuro
const darkMode = ref(false)

onMounted(() => {
  darkMode.value = window.matchMedia('(prefers-color-scheme: dark)').matches
  updateTheme()
})

function toggleTheme() {
  darkMode.value = !darkMode.value
  updateTheme()
}

function updateTheme() {
  document.documentElement.setAttribute('data-theme', darkMode.value ? 'dark' : 'light')
}

// 🌗 Logo dinámico
const logoSrc = computed(() =>
  darkMode.value ? '/logo-dark.png' : '/mihorario-logo.png'
)
</script>

<style scoped>
.login-wrapper {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background: linear-gradient(to bottom right, #e0f7fa, #f1f8e9);
  padding: 1rem;
}

[data-theme='dark'] .login-wrapper {
  background: #121212;
}

.welcome-text {
  font-size: 1rem;
  color: #666;
  margin-bottom: 1rem;
  text-align: center;
}

[data-theme='dark'] .welcome-text {
  color: #ccc;
}

.logo {
  width: 200px;
  margin-bottom: 1rem;
  animation: slideFade 0.6s ease;
}

@keyframes slideFade {
  from {
    opacity: 0;
    transform: translateY(-20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.toggle-theme {
  background: transparent;
  border: none;
  color: #3b82f6;
  margin-bottom: 1rem;
  cursor: pointer;
  font-size: 0.9rem;
  text-decoration: underline;
}

.login-form {
  background: white;
  padding: 2rem;
  border-radius: 12px;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.05);
  width: 100%;
  max-width: 320px;
  display: flex;
  flex-direction: column;
  gap: 1rem;
  animation: fadein 0.6s ease;
}

[data-theme='dark'] .login-form {
  background: #1e1e1e;
  color: #f0f0f0;
}

h2 {
  margin: 0;
  text-align: center;
}

.subtitle {
  font-size: 0.9rem;
  text-align: center;
  color: #777;
  margin-bottom: 0.5rem;
}

[data-theme='dark'] .subtitle {
  color: #bbb;
}

input {
  padding: 0.8rem;
  font-size: 1rem;
  border: 1px solid #ddd;
  border-radius: 6px;
}

[data-theme='dark'] input {
  background: #2a2a2a;
  color: #fff;
  border: 1px solid #555;
}

button {
  padding: 0.8rem;
  background: #3b82f6;
  color: white;
  border: none;
  font-weight: 600;
  border-radius: 6px;
  cursor: pointer;
  transition: background 0.3s;
}

button:hover {
  background: #2563eb;
}

.link-help {
  font-size: 0.85rem;
  color: #3b82f6;
  text-align: center;
  text-decoration: none;
}

.link-help:hover {
  text-decoration: underline;
}

.footer {
  margin-top: 1.5rem;
  font-size: 0.8rem;
  color: #999;
}

[data-theme='dark'] .footer {
  color: #bbb;
}

@keyframes fadein {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>
