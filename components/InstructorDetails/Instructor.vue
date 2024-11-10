<!-- Instructor.vue -->
<template>
    <div class="max-w-3xl mx-auto p-6 ml-3 m-3">
      <h2 class="text-2xl font-bold mb-4">Instructor</h2>
      
      <InstructorDetails :instructor="instructor" />
      <InstructorBio />
    </div>
  </template>
  
  <script setup>
  import InstructorDetails from './InstructorDetails.vue'
  import InstructorBio from './InstructorBio.vue'
  
  const instructor = {
    name: 'Loony Corn',
    title: 'An ex-Google, Stanford and Flipkart team',
    image: 'https://img-c.udemycdn.com/user/200_H/16442046_ea65_4.jpg',
    stats: [
      { icon: 'Star', value: '4.2', label: 'Instructor Rating' },
      { icon: 'Users', value: '28,414', label: 'Reviews' },
      { icon: 'GraduationCap', value: '168,336', label: 'Students' },
      { icon: 'BookOpen', value: '67', label: 'Courses' }
    ]
  }
  </script>
  