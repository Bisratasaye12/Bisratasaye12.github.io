<!-- TotalPrice.vue -->
<template>
    <div class="mt-8 flex items-center justify-between">
      <div>
        <span class="text-gray-600">Total:</span>
        <span class="text-xl font-bold ml-2">${{ total.toFixed(2) }}</span>
      </div>
    </div>
  </template>
  
  <script setup>
  defineProps({
    total: Number
  })
  </script>
  