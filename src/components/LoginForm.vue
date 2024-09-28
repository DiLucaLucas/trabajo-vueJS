<!-- Lógica del formulario -->
<script setup lang="ts">
import { ref } from "vue";
import { useRouter } from 'vue-router';
import { useUserStore } from '@/stores/user';  // Importamos el store de Pinia

// Referencia del formulario
const form = ref({
  user: '',
  password: '',
  remember: false
})

// Usamos el store para guardar los datos del usuario
const userStore = useUserStore();
const router = useRouter();

// Función para manejar el submit del formulario
const handleSubmit = () => {
  console.log(form.value);

  // Guardamos los datos en el store de Pinia
  userStore.setUser(form.value);

  // Nos redirige después de ingresar
  router.push({ name: 'Home' });
}
</script>

<!-- Estructura del formulario -->
<template>
  <div class="wrapper">
    <form @submit.prevent="handleSubmit">
      <h1>Login</h1>
      <div class="input-bx">
        <input v-model="form.user" type="text" placeholder="Usuario" required />
        <!-- Icono de usuario -->
        <ion-icon class="icon" name="person-circle"></ion-icon>
      </div>
      <div class="input-bx">
        <input v-model="form.password" type="password" placeholder="Contraseña" required />
        <!-- Icono de contraseña -->
        <ion-icon class="icon" name="lock-closed"></ion-icon>
      </div>
      <div class="remember-forgot">
        <label>
          <input v-model="form.remember" type="checkbox" />
          Recordarme
        </label>
        <a href="#">Olvidaste tu contraseña</a>
      </div>
      <button type="submit" class="btn">Ingresar</button>
    </form>
  </div>
</template>

<!-- Estilos del formulario -->
<style src="../assets/styles.css"></style>

