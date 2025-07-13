<template>
  <div class="text-white">
    <h1 class="text-3xl font-bold mb-6 text-yellow-400">Nueva cuenta</h1>

    <form @submit.prevent="onRegister">
      <!-- Nombre -->
      <div class="mb-4">
        <label for="name" class="block text-lime-400 font-medium">Nombre</label>
        <input
          v-model="myForm.fullName"
          type="text"
          id="name"
          name="name"
          class="w-full bg-gray-800 border border-lime-400 text-white rounded-md py-2 px-3 focus:outline-none focus:border-yellow-400"
          autocomplete="off"
        />
      </div>

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

      <!-- Olvidaste contraseña -->
      <div class="mb-6">
        <a href="#" class="text-lime-400 hover:underline text-sm">¿OLVIDASTE TU CONTRASEÑA?</a>
      </div>

      <!-- Botón -->
      <button
        type="submit"
        class="bg-yellow-400 hover:bg-yellow-500 text-black font-bold rounded-md py-2 px-4 w-full transition-all"
      >
        ¡CREAR CUENTA!
      </button>
    </form>

    <!-- Link a Login -->
    <div class="mt-6 text-center text-lime-400">
      <RouterLink :to="{ name: 'login' }" class="hover:underline">
        Iniciar sesión en una cuenta existente ¡INGRESA AQUÍ!
      </RouterLink>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { reactive } from 'vue';
import { useRouter } from 'vue-router';
import { useAuthStores } from '../stores/auth.stores';
import { useToast } from 'vue-toastification';

const router = useRouter();
const authStore = useAuthStores();
const toast = useToast();

const myForm = reactive({
  fullName: '',
  email: '',
  password: '',
});

const onRegister = async () => {
  const { ok, message } = await authStore.register(
    myForm.fullName,
    myForm.email,
    myForm.password
  );
  if (ok) return;
  toast.error(message);
};
</script>
