<template>
  <div class="text-white">
    <h1 class="text-3xl font-bold mb-6 text-yellow-400">Iniciar sesión</h1>

    <form @submit.prevent="onLogin">
      <!-- Correo -->
      <div class="mb-4">
        <label for="email" class="block text-lime-400 font-medium">Correo Electrónico</label>
        <input
          v-model="myForm.email"
          type="text"
          id="email"
          name="email"
          class="w-full bg-gray-800 border border-lime-400 text-white rounded-md py-2 px-3 focus:outline-none focus:border-yellow-400"
          autocomplete="off"
        />
      </div>

      <!-- Contraseña -->
      <div class="mb-4">
        <label for="password" class="block text-lime-400 font-medium">Contraseña</label>
        <input
          v-model="myForm.password"
          type="password"
          id="password"
          name="password"
          class="w-full bg-gray-800 border border-lime-400 text-white rounded-md py-2 px-3 focus:outline-none focus:border-yellow-400"
          autocomplete="off"
        />
      </div>

      <!-- Recordar -->
      <div class="mb-4 flex items-center">
        <input
          v-model="myForm.rememberMe"
          type="checkbox"
          id="remember"
          name="remember"
          class="accent-lime-400"
        />
        <label for="remember" class="text-lime-300 ml-2">Recordar Usuario</label>
      </div>

      <!-- ¿Olvidaste contraseña? -->
      <div class="mb-6">
        <a href="#" class="text-lime-400 hover:underline text-sm">¿Olvidaste tu contraseña burro?</a>
      </div>

      <!-- Botón -->
      <button
        type="submit"
        class="bg-yellow-400 hover:bg-yellow-500 text-black font-bold rounded-md py-2 px-4 w-full transition-all"
      >
        Ingresar
      </button>
    </form>

    <!-- Registro -->
    <div class="mt-6 text-center text-lime-400">
      <RouterLink :to="{ name: 'register' }" class="hover:underline">
        Crear nueva cuenta ¡Regístrate aquí!
      </RouterLink>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { reactive, watchEffect } from 'vue';
import { useRouter } from 'vue-router';
import { useAuthStores } from '../stores/auth.stores';
import { useToast } from 'vue-toastification';

const router = useRouter();
const authStore = useAuthStores();
const toast = useToast();

const myForm = reactive({
  email: '',
  password: '',
  rememberMe: false,
});

const onLogin = async () => {
  const ok = await authStore.login(myForm.email, myForm.password);

  if (myForm.rememberMe) {
    localStorage.setItem('email', myForm.email);
  } else {
    localStorage.removeItem('email');
  }

  if (ok) return;
  toast.error('E-mail/Contraseña ¡NO SON CORRECTOS!');
};

watchEffect(() => {
  const email = localStorage.getItem('email');
  if (email) {
    myForm.email = email;
    myForm.rememberMe = true;
  }
});
</script>
