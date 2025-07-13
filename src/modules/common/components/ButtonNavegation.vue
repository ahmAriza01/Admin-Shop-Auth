<template>
  <div class="flex justify-center py-10 bg-black space-x-3">
    <!-- Botón Anterior -->
    <button
      :disabled="isFirstPage"
      @click="$router.push({ query: { page: page - 1 } })"
      class="flex justify-center items-center space-x-1.5 px-4 py-1.5 text-black font-semibold bg-yellow-400 disabled:bg-gray-700 disabled:text-gray-400 rounded-lg hover:bg-yellow-500 transition-all"
    >
      <ArrowLeft />
      <span>Anterior</span>
    </button>

    <!-- Botón Siguiente -->
    <button
      :disabled="hasMoreData"
      @click="$router.push({ query: { page: page + 1 } })"
      class="flex justify-center items-center space-x-1.5 px-4 py-1.5 text-black font-semibold bg-yellow-400 disabled:bg-gray-700 disabled:text-gray-400 rounded-lg hover:bg-yellow-500 transition-all"
    >
      <span>Siguiente</span>
      <ArrowRight />
    </button>
  </div>
</template>

<script setup lang="ts">
import ArrowRight from '@/icon/ArrowRight.vue';
import ArrowLeft from '@/icon/ArrowLeft.vue';

interface Props {
  page: number;
  isFirstPage: boolean;
  hasMoreData: boolean;
}

defineProps<Props>();
</script>

<style scoped>
/* Si deseas animaciones más vistosas puedes agregar aquí */
</style>
