<template>
    <div class="max-w-lg mx-auto bg-white rounded-lg border border-gray-200 shadow-sm m-5 ml-3">
      <div class="p-4 bg-gray-50 rounded-t-lg border-b border-gray-200">
        <p class="text-gray-700 text-lg">
          Prepare for your certifications with this course. 
          <a href="#" class="text-indigo-600 hover:text-indigo-800 font-medium">Learn more</a>
        </p>
      </div>
  
      <div class="p-4">
        <ul class="space-y-4 relative" :style="listStyle">
          <li v-for="(cert, index) in certifications" :key="cert.id" 
              class="flex items-center gap-4"
              :style="getCertStyle(index)">
            <div class="w-12 h-12 rounded-full bg-gray-100 p-1 flex items-center justify-center shrink-0">
              <img 
                :src="cert.icon" 
                :alt="`${cert.title} icon`"
                class="w-8 h-8 object-contain"
              />
            </div>
            <div class="min-w-0">
              <h3 class="text-indigo-600 font-medium truncate">{{ cert.title }}</h3>
              <p class="text-lg text-gray-600 truncate">Issued by {{ cert.issuer }}</p>
            </div>
          </li>
        </ul>
  
        <button 
          @click="toggleExpand"
          class="mt-4 text-indigo-600 hover:text-indigo-800 font-medium text-lg flex items-center gap-1"
        >
          {{ expanded ? 'Show less' : 'Show more' }}
          <ChevronDownIcon 
            class="w-4 h-4 transition-transform duration-200"
            :class="{ 'transform rotate-180': expanded }"
          />
        </button>
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref, computed } from 'vue'
  import { ChevronDownIcon } from 'lucide-vue-next'
  
  const expanded = ref(false)
  
  const certifications = [
    {
      id: 1,
      title: 'Professional Data Engineer',
      issuer: 'Google Cloud',
      icon: 'https://hebbkx1anhila5yf.public.blob.vercel-storage.com/image-Jl41yI2DVVTFId8fSNUY5uJbUpKdsZ.png'
    },
    {
      id: 2,
      title: 'Professional Cloud Architect',
      issuer: 'Google Cloud',
      icon: 'https://hebbkx1anhila5yf.public.blob.vercel-storage.com/image-Jl41yI2DVVTFId8fSNUY5uJbUpKdsZ.png'
    }
  ]
  
  const toggleExpand = () => {
    expanded.value = !expanded.value
  }
  
  const listStyle = computed(() => ({
    height: expanded.value ? 'auto' : '84px',
    overflow: 'hidden',
    transition: 'height 0.3s ease-in-out'
  }))
  
  const getCertStyle = (index) => {
    if (expanded.value || index === 0) return {}
    return {
      position: 'absolute',
      top: '52px',
      left: '0',
      right: '0',
      opacity: '0.5',
      pointerEvents: 'none'
    }
  }
  </script>
  
  <style scoped>
  ul {
    transition: all 0.3s ease-in-out;
  }
  
  li {
    transition: opacity 0.3s ease-in-out, transform 0.3s ease-in-out;
  }
  </style>