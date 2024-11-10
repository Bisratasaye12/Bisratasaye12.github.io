<!-- InstructorBio.vue -->
<template>
    <div class="space-y-4">
      <p>
        Loonycorn is us, Janani Ravi and Vitthal Srinivasan. Between us, we have studied at Stanford, been admitted to 
        IIM Ahmedabad and have spent years working in tech, in the Bay Area, New York, Singapore and Bangalore.
      </p>
      
      <div class="relative">
        <p :class="{'blur-sm': !isExpanded}" class="transition-all duration-300">
          Janani: 7 years at Google (New York, Singapore); Studied at Stanford; also worked at Flipkart and Microsoft
        </p>
        <div v-if="!isExpanded" class="absolute inset-0 bg-gradient-to-b from-transparent to-white"></div>
      </div>
      
      <transition
        name="expand"
        @enter="startTransition"
        @after-enter="endTransition"
        @before-leave="startTransition"
        @after-leave="endTransition"
      >
        <div v-if="isExpanded" class="space-y-4">
          <p>
            Vitthal: Also Google (Singapore) and studied at Stanford; Flipkart, Credit Suisse and INSEAD too
          </p>
          <p>
            We think we might have hit upon a neat way of teaching complicated tech courses in a funny, practical, engaging 
            way, which is why we are so excited to be here on Udemy!
          </p>
        </div>
      </transition>
  
      <button 
        @click="toggleExpand"
        class="flex items-center gap-1 text-purple-600 hover:text-purple-700 transition-colors"
      >
        <span>Show {{ isExpanded ? 'less' : 'more' }}</span>
        <ChevronDown 
          :class="['w-4 h-4 transition-transform', isExpanded ? 'rotate-180' : '']"
        />
      </button>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue'
  import { ChevronDown } from 'lucide-vue-next'
  
  const isExpanded = ref(false)
  
  const toggleExpand = () => {
    isExpanded.value = !isExpanded.value
  }
  
  const startTransition = (element) => {
    element.style.height = 'auto'
    const height = element.getBoundingClientRect().height
    element.style.height = '0'
    // Force reflow
    element.offsetHeight
    element.style.height = height + 'px'
  }
  
  const endTransition = (element) => {
    element.style.height = ''
  }
  </script>
  