<template>
    <div class="flex items-center gap-2 my-2">
      <div class="flex">
        <StarIcon v-for="i in Math.floor(stars)" :key="i" class="w-5 h-5 text-yellow-400 fill-current" />
        <StarIcon v-if="halfStar" class="w-5 h-5 text-yellow-400 fill-current opacity-50" />
      </div>
      <span class="text-sm text-gray-500">{{ time }}</span>
    </div>
  </template>
  
  <script setup>
  import { StarIcon } from 'lucide-vue-next'
  
  const props = defineProps({
    stars: Number,
    time: String
  })
  
  const halfStar = props.stars % 1 !== 0
  </script>
  