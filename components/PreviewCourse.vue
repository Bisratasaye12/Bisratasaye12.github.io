<template>
    <div 
      :class="[scrolling ? 'lg:fixed lg:top-6' : 'lg:absolute top-3']"
      class="bg-white m-4 lg:z-20 border-0.5 border-white p-[1px] w-full lg:shadow-lg lg:w-[350px] lg:right-10 xl:right-20 2xl:right-40 mt-4 border-black shadow-md"
      style="margin-top: 5rem ;z-index: 1;"

    >
      <div class="relative">
        <!-- Video Preview -->
        <div v-if="!scrolling" class="w-full aspect-video">
          <video
            ref="videoPlayer"
            class="w-full h-full object-cover"
            :src="previewVideoUrl"
            muted
            loop
            playsinline
          ></video>
          <div class="absolute inset-0 flex items-center justify-center">
            <button @click="toggleVideo" class="bg-black bg-opacity-50 text-white p-4 rounded-full">
              <svg v-if="!isPlaying" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" class="w-8 h-8">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14.752 11.168l-3.197-2.132A1 1 0 0010 9.87v4.263a1 1 0 001.555.832l3.197-2.132a1 1 0 000-1.664z" />
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
              </svg>
              <svg v-else xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" class="w-8 h-8">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 9v6m4-6v6m7-3a9 9 0 11-18 0 9 9 0 0118 0z" />
              </svg>
            </button>
          </div>
        </div>
      </div>
  
      <!-- Price and Other Content -->
      <div class="px-6 mt-5 pb-6 space-y-4 rounded-lg">
        <h2 class="text-4xl text-gray-900 leading-10 font-bold">$74.99</h2>
        <button class="bg-violet-500 font-bold hover:bg-violet-600 w-full flex justify-center items-center p-3 text-white">
          Add to cart
        </button>
        <button class="border border-black font-bold hover:bg-black/20 w-full flex justify-center items-center p-3 text-black">
          Buy now
        </button>
        <p class="text-gray-500 font-sans text-center text-xs">30-Day Money-Back Guarantee</p>
  
        <div class="w-full">
          <h2 class="text-sm font-bold mb-2 text-gray-900">This course includes:</h2>
          <ul class="space-y-2 text-sm">
            <li v-for="(feature, index) in features" :key="index" class="flex items-center space-x-3">
              <div v-html="feature.icon" class="w-5 h-5 text-gray-900"></div>
              <span class="text-gray-700">{{ feature.text }}</span>
            </li>
          </ul>
        </div>
  
        <!-- Coupon Section -->
        <div class="border-t border-gray-200 pt-4">
          <div class="flex items-center justify-between mb-2">
            <span class="text-sm text-gray-600">LETLEARNNOW is applied</span>
            <button class="text-violet-600 hover:text-violet-700">
              <XMarkIcon class="h-5 w-5" />
            </button>
          </div>
          <div class="flex space-x-2">
            <input
              type="text"
              placeholder="Enter Coupon"
              class="flex-1 border border-gray-300 rounded px-3 py-2 text-sm focus:outline-none focus:border-violet-500"
            />
            <button class="bg-violet-500 text-white px-4 py-2 rounded text-sm hover:bg-violet-600">
              Apply
            </button>
          </div>
        </div>
  
        <!-- Training Section -->
        <div class="border-t border-gray-200 pt-4">
          <h3 class="font-semibold text-gray-900 mb-2">Training 5 or more people?</h3>
          <p class="text-sm text-gray-600 mb-3">Get your team access to 27,000+ top Udemy courses anytime, anywhere.</p>
          <button class="w-full border border-gray-300 rounded py-2 text-sm font-medium hover:bg-gray-50">
            Try Udemy Business
          </button>
        </div>
  
        <!-- Action Buttons -->
        <div class="flex justify-between border-t border-gray-200 pt-4">
          <button class="text-sm text-gray-600 hover:text-gray-900">Share</button>
          <button class="text-sm text-gray-600 hover:text-gray-900">Gift this course</button>
          <button class="text-sm text-gray-600 hover:text-gray-900">Apply Coupon</button>
        </div>
      </div>
    </div>
  </template>
  
  <script setup lang="ts">
  import { ref, onMounted, onUnmounted } from 'vue'
  import { XMarkIcon } from '@heroicons/vue/24/outline'
  
  const scrolling = ref(false)
  const isPlaying = ref(false)
  const videoPlayer = ref<HTMLVideoElement | null>(null)
  
  const previewVideoUrl = 'https://www.youtube.com/watch?v=047io79aP2g'
  const courseThumbnail = 'https://hebbkx1anhila5yf.public.blob.vercel-storage.com/image-Jl41yI2DVVTFId8fSNUY5uJbUpKdsZ.png'
  
  const features = [
    { 
      icon: `<svg class="size-5" fill="currentColor" viewBox="0 0 491.52 491.52" xmlns="http://www.w3.org/2000/svg"><path d="M0,0v327.68h491.52V0H0z M471.04,307.2H20.48V20.48h450.56V307.2z"/><path d="M194.56,87.77v141.9l122.88-70.95L194.56,87.77z M215.04,123.25l61.44,35.47l-61.44,35.47V123.25z"/></svg>`,
      text: '28 hours on-demand video'
    },
    {
      icon: `<svg class="size-5" fill="currentColor" viewBox="0 0 24 24"><path d="M19 5v14H5V5h14m0-2H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2z"/><path d="M14 17H7v-2h7v2zm3-4H7v-2h10v2zm0-4H7V7h10v2z"/></svg>`,
      text: '25 articles'
    },
    {
      icon: `<svg class="size-5" fill="currentColor" viewBox="0 0 24 24"><path d="M19 9h-4V3H9v6H5l7 7 7-7zM5 18v2h14v-2H5z"/></svg>`,
      text: '48 downloadable resources'
    },
    {
      icon: `<svg class="size-5" fill="currentColor" viewBox="0 0 24 24"><path d="M21 3H3c-1.1 0-2 .9-2 2v12c0 1.1.9 2 2 2h5v2h8v-2h5c1.1 0 1.99-.9 1.99-2L23 5c0-1.1-.9-2-2-2zm0 14H3V5h18v12z"/></svg>`,
      text: 'Access on mobile and TV'
    },
    {
      icon: `<svg class="size-5" fill="currentColor" viewBox="0 0 24 24"><path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm0 18c-4.41 0-8-3.59-8-8s3.59-8 8-8 8 3.59 8 8-3.59 8-8 8z"/><path d="M12 17c2.76 0 5-2.24 5-5s-2.24-5-5-5-5 2.24-5 5 2.24 5 5 5z"/></svg>`,
      text: 'Full lifetime access'
    },
    {
      icon: `<svg class="size-5" fill="currentColor" viewBox="0 0 24 24"><path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zm0 16H5V5h14v14z"/><path d="M7.5 13h2v2H11V9H9.5v2.5h-2V9H6v6h1.5z"/><path d="M18 11c0-1.1-.9-2-2-2h-2.5v6H15v-2h.5l1 2H18l-1.1-2.2c.6-.3 1.1-1 1.1-1.8zm-3 0h1c.3 0 .5.2.5.5s-.2.5-.5.5h-1v-1z"/></svg>`,
      text: 'Certificate of completion'
    }
  ]
  
  const toggleVideo = () => {
    if (videoPlayer.value) {
      if (isPlaying.value) {
        videoPlayer.value.pause()
      } else {
        videoPlayer.value.play()
      }
      isPlaying.value = !isPlaying.value
    }
  }
  
  const handleScroll = () => {
    scrolling.value = window.scrollY > 100
  }
  
  onMounted(() => {
    window.addEventListener('scroll', handleScroll)
    handleScroll() // Initial check
  })
  
  onUnmounted(() => {
    window.removeEventListener('scroll', handleScroll)
  })
  </script>
  
  <style scoped>
  .size-5 {
    width: 1.25rem;
    height: 1.25rem;
  }
  </style>