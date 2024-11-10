<!-- FrequentlyBoughtTogether.vue -->
<template>
    <div class="max-w-3xl mx-auto p-6 border rounded-lg ml-3 m-3">
      <h2 class="text-2xl font-bold mb-6">Frequently Bought Together</h2>
      
      <div class="space-y-4">
        <CourseCard v-for="(course, index) in courses" :key="course.id" :course="course" :index="index" :courses="courses" />
      </div>
  
      <div class="flex item-start gap-10">
        <TotalPrice :total="total" />
      <AddToCartButton :addToCart="addToCart" />
      </div>
    </div>
  </template>
  
  <script setup>
  import { computed } from 'vue'
  import CourseCard from './CourseCard.vue'
  import TotalPrice from './TotalPrice.vue'
  import AddToCartButton from './AddToCartButton.vue'
  
  const courses = [
    {
      id: 1,
      title: 'GCP: Complete Google Data Engineer and Cloud Architect Guide',
      rating: 4.4,
      ratings: 5121,
      price: 74.99,
      author: 'Google Cloud Experts Cloud Architect',
      image: 'https://img-c.udemycdn.com/course/240x135/1299656_ad0c.jpg'
    },
    {
      id: 2,
      title: 'Ultimate Google Certified Professional Cloud Architect 2024',
      rating: 4.3,
      ratings: 5121,
      price: 19.99,
      author: 'Google Cloud Experts Cloud Architect, Google Cloud Platform',
      image: 'https://img-c.udemycdn.com/course/240x135/1343890_c3c3_15.jpg'
    },
    {
      id: 3,
      title: 'Ultimate Google Cloud Certifications: All in one Bundle',
      rating: 4.4,
      ratings: 3495,
      price: 69.99,
      author: 'Google Cloud Experts Cloud Architect, Google Cloud Platform',
      image: 'https://img-c.udemycdn.com/course/240x135/2459706_d13a_6.jpg'
    }
  ]
  
  const total = computed(() => {
    return courses.reduce((sum, course) => sum + course.price, 0)
  })
  
  const addToCart = () => {
    console.log('Adding courses to cart:', courses)
  }
  </script>
  