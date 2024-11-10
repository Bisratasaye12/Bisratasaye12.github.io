<!-- InstructorDetails.vue -->
<template>
    <div class="space-y-4">
      <h3 class="text-xl font-semibold text-purple-600">
        <a href="#" class="hover:underline">{{ instructor.name }}</a>
      </h3>
      <p class="text-gray-600">{{ instructor.title }}</p>
      <div class="flex items-start gap-6">
        <img :src="instructor.image" :alt="instructor.name" class="w-32 h-32 rounded-full object-cover" />
        <InstructorStats :stats="instructor.stats" />
      </div>
    </div>
  </template>
  
  <script setup>
  import InstructorStats from './InstructorStats.vue'
  
  defineProps({
    instructor: Object
  })
  </script>
  