<!-- InstructorStats.vue -->
<template>
    <div class="grid grid-cols-1 gap-4">
      <div v-for="(stat, index) in stats" :key="index" class="flex items-center gap-2">
        <component :is="stat.icon" class="w-5 h-5 text-gray-600" />
        <span class="font-medium">{{ stat.value }}</span>
        <span class="text-gray-600">{{ stat.label }}</span>
      </div>
    </div>
  </template>
  
  <script setup>
  defineProps({
    stats: Array
  })
  </script>
  