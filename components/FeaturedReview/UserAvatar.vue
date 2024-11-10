<template>
    <div class="flex items-center gap-4">
      <img
        src='https://hebbkx1anhila5yf.public.blob.vercel-storage.com/image-Jl41yI2DVVTFId8fSNUY5uJbUpKdsZ.png'
        alt="User avatar"
        class="w-12 h-12 rounded-full object-cover"
      />
      <div>
        <h3 class="font-medium text-gray-900">{{ name }}</h3>
        <div class="text-sm text-gray-600">
          <span>{{ courses }}</span>
          <span class="mx-2">•</span>
          <span>{{ reviews }}</span>
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
  defineProps({
    name: String,
    avatarSrc: String,
    courses: String,
    reviews: String
  })
  </script>
  