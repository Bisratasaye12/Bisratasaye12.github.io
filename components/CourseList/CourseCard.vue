<!-- CourseCard.vue -->
<template>
    <div class="flex items-start gap-4 p-4 border rounded-lg hover:shadow-lg transition-shadow">
      <img :src="course.image" :alt="course.title" class="w-20 h-20 object-cover rounded" />
  
      <div class="flex-1 min-w-0">
        <h3 class="font-medium text-lg">{{ course.title }}</h3>
  
        <CourseRating :rating="course.rating" :students="course.students" />
  
        <div class="flex items-center gap-2 mt-1 text-sm text-gray-600">
          <span>{{ course.hours }} total hours</span>
          <span>•</span>
          <span>Updated {{ course.updated }}</span>
        </div>
      </div>
  
      <div class="flex flex-col items-end gap-2">
        <span class="font-bold">${{ course.price.toFixed(2) }}</span>
        <button @click="$emit('toggle-wishlist', course.id)"
                class="p-2 rounded-full hover:bg-gray-100 transition-colors">
          <Heart :class="['w-5 h-5', course.isWishlisted ? 'fill-red-500 text-red-500' : 'text-gray-400']" />
        </button>
      </div>
    </div>
  </template>
  
  <script setup>
  import { Heart } from 'lucide-vue-next'
  import CourseRating from './CourseRating.vue'
  defineProps(['course'])
  </script>
  