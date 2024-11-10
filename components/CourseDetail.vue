d<template>
  <div class="min-h-[300px] bg-gray-900 text-white p-8">
    <nav class="flex items-center space-x-2 text-sm mb-6">
      <a href="#" class="text-blue-400 hover:text-blue-300">Development</a>
      <span class="text-gray-500">&gt;</span>
      <a href="#" class="text-blue-400 hover:text-blue-300">Software Testing</a>
      <span class="text-gray-500">&gt;</span>
      <span class="text-gray-400">Google Cloud Professional Data Engineer</span>
    </nav>

    <h1 class="text-4xl font-bold mb-4">
      GCP: Complete Google Data Engineer and Cloud Architect Guide
    </h1>

    <p class="text-gray-300 text-lg mb-6">
      The Google Cloud for ML with TensorFlow, Big Data with Managed Hadoop
    </p>

    <div class="flex items-center space-x-4 mb-4">
      <span class="text-yellow-500 font-bold">3.1</span>
      <div class="flex items-center">
        <StarIcon v-for="i in 3" :key="`full-${i}`" class="w-4 h-4 text-yellow-500 fill-current" />
        <StarHalfIcon class="w-4 h-4 text-yellow-500 fill-current" />
        <StarIcon class="w-4 h-4 text-gray-600 fill-current" />
      </div>
      <a href="#" class="text-blue-400 hover:text-blue-300">(7,355 ratings)</a>
      <span class="text-gray-400">50,321 students</span>
    </div>

    <div class="mb-4">
      <span class="text-gray-400">Created by</span>
      <a href="#" class="text-blue-400 hover:text-blue-300 ml-1">Loony Corn</a>
    </div>

    <div class="flex items-center space-x-4 text-sm text-gray-400">
      <div class="flex items-center">
        <ClockIcon class="w-4 h-4 mr-1" />
        Last updated 7/2018
      </div>
      <div class="flex items-center">
        <GlobeIcon class="w-4 h-4 mr-1" />
        English
      </div>
      <div class="flex items-center">
        <MessageSquareIcon class="w-4 h-4 mr-1" />
        English [Auto], French [Auto], 
        {{ showMoreLanguages ? 'Spanish [Auto], Portuguese [Auto], German [Auto], Italian [Auto], Russian [Auto], Chinese [Auto], Japanese [Auto]' : '' }}
        <button 
          @click="showMoreLanguages = !showMoreLanguages"
          class="text-blue-400 hover:text-blue-300 ml-1"
        >
          {{ showMoreLanguages ? 'less' : '9 more' }}
        </button>
      </div>
    </div>
  </div>
</template>

<script setup >

import { StarIcon, StarHalfIcon, ClockIcon, GlobeIcon, MessageSquareIcon } from 'lucide-vue-next'



const showMoreLanguages = ref(false)
</script>