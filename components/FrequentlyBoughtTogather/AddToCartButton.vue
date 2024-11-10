<!-- AddToCartButton.vue -->
<template>
    <button @click="addToCart"
            class="px-6 py-2 bg-purple-600 text-white rounded-lg hover:bg-purple-700 transition-colors">
      Add all to cart
    </button>
  </template>
  
  <script setup>
  defineProps({
    addToCart: Function
  })
  </script>
  