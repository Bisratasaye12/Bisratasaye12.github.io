
<template>
    <div class="flex items-center gap-2 mt-1">
      <span class="font-bold">{{ rating }}</span>
      <div class="flex">
        <StarIcon v-for="i in Math.floor(rating)" :key="i" class="w-4 h-4 fill-yellow-400 text-yellow-400" />
        <StarIcon v-if="rating % 1 >= 0.5" class="w-4 h-4 fill-yellow-400 text-yellow-400" />
      </div>
      <span class="text-gray-600">{{ students.toLocaleString() }}</span>
    </div>
  </template>
  
  <script setup>
  import { Star as StarIcon } from 'lucide-vue-next'
  defineProps(['rating', 'students'])
  </script>
  