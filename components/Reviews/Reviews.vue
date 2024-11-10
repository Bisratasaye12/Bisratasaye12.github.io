<!-- MainReviewSection.vue -->
<template>
    <div class="max-w-4xl mx-auto p-6">
      <CourseRating :rating="rating" :totalRatings="totalRatings" />
      <ReviewList />
    </div>
  </template>
  
  <script setup>
  import CourseRating from './CourseRating.vue'
  import ReviewList from './ReviewList.vue'
  
  const rating = '3.1'
  const totalRatings = '7K'
  </script>
  