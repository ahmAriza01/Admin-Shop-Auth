<template>
  <div>
    <!-- Header Navbar -->
    <nav class="fixed top-0 left-0 z-20 w-full border-b border-lime-500 bg-black py-2.5 px-6 sm:px-4 shadow-md">
      <div class="container mx-auto flex max-w-6xl flex-wrap items-center justify-between">
        <a href="#" class="flex items-center">
          <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
            stroke="currentColor" class="mr-3 h-6 text-yellow-400 sm:h-9">
            <path stroke-linecap="round" stroke-linejoin="round"
              d="M21 7.5l-9-5.25L3 7.5m18 0l-9 5.25m9-5.25v9l-9 5.25M3 7.5l9 5.25M3 7.5v9l9 5.25m0-9v9" />
          </svg>

          <span class="self-center whitespace-nowrap text-xl font-bold text-white">Termcode</span>
        </a>

        <div class="mt-2 sm:mt-0 sm:flex md:order-2">
          <template v-if="!authStore.isAuthenticated">
            <!-- Login Button -->
            <RouterLink to="/auth/login"
              class="mr-3 hidden border border-lime-400 py-1.5 px-6 text-sm font-medium text-lime-400 hover:bg-lime-500 hover:text-black focus:outline-none focus:ring-2 focus:ring-lime-400 md:inline-block rounded-lg">
              Iniciar sesión
            </RouterLink>

            <RouterLink to="/auth/register"
              class="mr-3 hidden bg-yellow-400 py-1.5 px-6 text-sm font-bold text-black hover:bg-yellow-500 focus:outline-none focus:ring-2 focus:ring-yellow-400 md:mr-0 md:inline-block rounded-lg">
              Crear cuenta
            </RouterLink>
          </template>

          <template v-if="authStore.isAuthenticated">
            <RouterLink
            v-if="authStore.isAdmin"
            to="/admin"
              class="mr-3 hidden border border-lime-400 py-1.5 px-6 text-sm font-medium text-lime-400 hover:bg-lime-500 hover:text-black focus:outline-none focus:ring-2 focus:ring-lime-400 md:inline-block rounded-lg">
              Admin
            </RouterLink>

            <button
              @click="authStore.logout()"
              type="button"
              class="mr-3 hidden bg-yellow-400 py-1.5 px-6 text-sm font-bold text-black hover:bg-yellow-500 focus:outline-none focus:ring-2 focus:ring-yellow-400 md:mr-0 md:inline-block rounded-lg">
              Cerrar sesión
            </button>
            <!--Register button-->
          </template>
          <button data-collapse-toggle="navbar-sticky" type="button"
            class="inline-flex items-center rounded-lg p-2 text-sm text-lime-400 hover:bg-gray-800 focus:outline-none focus:ring-2 focus:ring-yellow-400 md:hidden"
            aria-controls="navbar-sticky" aria-expanded="false">
            <span class="sr-only">Open main menu</span>
            <svg class="h-6 w-6" fill="currentColor" viewBox="0 0 20 20"
              xmlns="http://www.w3.org/2000/svg">
              <path fill-rule="evenodd"
                d="M3 5a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1zM3 10a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1zM3 15a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1z"
                clip-rule="evenodd"></path>
            </svg>
          </button>
        </div>

        <!-- Menu Items -->
        <div class="hidden w-full items-center justify-between md:order-1 md:flex md:w-auto" id="navbar-sticky">
          <ul
            class="mt-4 flex flex-col rounded-lg border border-lime-400 bg-gray-900 p-4 md:mt-0 md:flex-row md:space-x-8 md:border-0 md:bg-black md:text-sm md:font-medium">
            <li>
              <a href="#" class="block rounded py-2 pl-3 pr-4 text-yellow-400 font-bold hover:text-white md:p-0">
                Home
              </a>
            </li>
            <li>
              <a href="#" class="block rounded py-2 pl-3 pr-4 text-lime-400 hover:text-yellow-400 md:p-0">
                About
              </a>
            </li>
            <li>
              <a href="#" class="block rounded py-2 pl-3 pr-4 text-lime-400 hover:text-yellow-400 md:p-0">
                Services
              </a>
            </li>
            <li>
              <a href="#" class="block rounded py-2 pl-3 pr-4 text-lime-400 hover:text-yellow-400 md:p-0">
                Contact
              </a>
            </li>
          </ul>
        </div>
      </div>
    </nav>
  </div>
</template>

<script setup lang="ts">
import { useAuthStores } from '@/modules/auth/stores/auth.stores';
const authStore = useAuthStores();
</script>
