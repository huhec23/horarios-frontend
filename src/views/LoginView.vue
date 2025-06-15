<template>
  <div class="login-page">
    <LoginForm />
  </div>
</template>

<script setup>
import LoginForm from '@/components/LoginForm.vue'
</script>

<style scoped>
.login-page {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background-color: #f3f4f6;
}
</style>
