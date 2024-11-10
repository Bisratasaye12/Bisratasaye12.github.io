<!-- ReviewItem.vue -->
<template>
    <div class="border-b pb-6">
      <div class="flex items-start justify-between">
        <div class="flex items-center gap-3">
          <div class="w-10 h-10 rounded-full bg-gray-800 text-white flex items-center justify-center font-semibold">
            {{ review.initials }}
          </div>
          <div>
            <div class="font-medium">{{ review.name }}</div>
            <div class="flex items-center gap-2">
              <div class="flex">
                <Star v-for="i in 5" :key="i" :class="['w-4 h-4', i <= review.rating ? 'text-orange-500 fill-orange-500' : 'text-gray-300']" />
              </div>
              <span class="text-sm text-gray-500">{{ review.timeAgo }}</span>
            </div>
          </div>
        </div>
        <button class="text-gray-500 hover:text-gray-700">
          <MoreVertical class="w-5 h-5" />
        </button>
      </div>
      
      <p class="mt-3 text-gray-600">{{ review.content }}</p>
      
      <div class="mt-4 flex items-center gap-4">
        <span class="text-sm text-gray-500">Helpful?</span>
        <button 
          class="flex items-center gap-1 text-sm text-gray-500 hover:text-gray-700"
          @click="handleHelpful(true)"
        >
          <ThumbsUp class="w-4 h-4" :class="{ 'text-blue-500': review.userVote === 'up' }" />
        </button>
        <button 
          class="flex items-center gap-1 text-sm text-gray-500 hover:text-gray-700"
          @click="handleHelpful(false)"
        >
          <ThumbsDown class="w-4 h-4" :class="{ 'text-red-500': review.userVote === 'down' }" />
        </button>
      </div>
    </div>
  </template>
  
  <script setup>
  import { Star, ThumbsUp, ThumbsDown, MoreVertical } from 'lucide-vue-next'
  
  defineProps({
    review: Object,
    onHelpful: Function
  })
  
  const handleHelpful = (isHelpful) => {
    onHelpful(isHelpful)
  }
  </script>
  