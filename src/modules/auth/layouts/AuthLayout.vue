<template>
  <!-- Component -->
  <div class="bg-black flex justify-center items-center h-screen">
    <!-- Left: Image -->
    <div class="w-1/2 h-screen hidden lg:block">
      <img
        :src="loginImg"
        alt="Login Image"
        class="object-cover w-full h-full"
      />
    </div>
    <!-- Right: Login Form -->
    <div class="lg:p-36 md:p-52 sm:p-20 p-8 w-full lg:w-1/2">
      <RouterView />
    </div>
  </div>
</template>

<script setup>
import loginImg from '@/assets/img/login.jpg' // Asegúrate de que la imagen exista
</script>
