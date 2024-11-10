<template>
    <div class="max-w-3xl mx-auto p-6 border border-gray-200 rounded-lg m-3 ml-3">
      <h2 class="text-2xl font-semibold text-gray-900 mb-6">What you'll learn</h2>
      
      <div class="grid md:grid-cols-2 gap-4">
        <div v-for="(objective, index) in learningObjectives" 
             :key="index"
             class="flex items-start gap-3">
          <CheckIcon class="w-5 h-5 mt-0.5 text-gray-600 shrink-0" />
          <span class="text-gray-700">{{ objective }}</span>
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
  import { CheckIcon } from 'lucide-vue-next'
  
  const learningObjectives = [
    'Deploy Managed Hadoop apps on the Google Cloud',
    'Make informed decisions about Containers, VMs and AppEngine',
    'Build deep learning models on the cloud using TensorFlow',
    'Use big data technologies such as BigTable, Dataflow, Apache Beam and Pub/Sub'
  ]
  </script>