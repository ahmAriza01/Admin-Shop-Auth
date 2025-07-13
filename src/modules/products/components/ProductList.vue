<template>
  <section class="py-10 bg-black">
    <div class="mx-auto grid max-w-6xl grid-cols-1 gap-6 p-6 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4">
      <ProductCard
        v-for="product in products"
        :key="product.id"
        :product="product"
      />
    </div>
  </section>
</template>

<script setup lang="ts">
import type { Product } from '../interfaces/product';
import ProductCard from './ProductCard.vue';

interface Props {
  products: Product[]
}
defineProps<Props>();
</script>

<style scoped>
/* Si luego quieres agregar glow al hover en el grid:
.product-card:hover {
  box-shadow: 0 0 10px #39ff14;
}
*/
</style>
