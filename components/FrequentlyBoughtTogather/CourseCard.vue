<!-- CourseCard.vue -->
<template>
    <div class="flex items-center gap-5">
      <div class="relative">
        <img :src="course.image" :alt="course.title" class="w-32 h-24 object-cover rounded-lg" />
        <div style="z-index: 1;" v-if="index < courses.length - 1" class="absolute -bottom-8 left-1/2 -translate-x-1/2 w-8 h-8 bg-white rounded-full border shadow-sm flex items-center justify-center">
          <PlusIcon class="w-7 h-7 text-gray-600 " />
        </div>
      </div>
      <div class="flex-1 min-w-0">
        <h3 class="font-medium">{{ course.title }}</h3>
        <CourseRating :rating="course.rating" :ratings="course.ratings" />
        <div class="text-sm text-gray-600 mt-1">{{ course.author }}</div>
      </div>
      <div class="text-lg font-bold">${{ course.price.toFixed(2) }}</div>
    </div>
  </template>
  
  <script setup>
  import { Plus as PlusIcon } from 'lucide-vue-next'
  import CourseRating from './CourseRating.vue'
  
  defineProps({
    course: Object,
    index: Number,
    courses: Array
  })
  </script>
  