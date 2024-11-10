<!-- CourseRating.vue -->
<template>
    <div class="mb-8">
      <div class="flex items-center gap-2 text-xl font-semibold">
        <Star class="w-6 h-6 text-orange-500 fill-orange-500" />
        <span>{{ rating }} course rating</span>
        <span class="text-gray-500">•</span>
        <span>{{ totalRatings }} ratings</span>
      </div>
    </div>
  </template>
  
  <script setup>
  defineProps({
    rating: String,
    totalRatings: String
  })
  </script>
  