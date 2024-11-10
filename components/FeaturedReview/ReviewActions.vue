<template>
  <div class="items-center gap-4">
    <span class="text-sm text-gray-500 mb-3">Was this review helpful?</span>
    <div class="flex gap-2">
      <button class="p-2 border rounded-full hover:bg-gray-50" aria-label="Mark review as helpful">
        <ThumbsUpIcon class="w-4 h-4 text-gray-600" />
      </button>
      <button class="p-2 border rounded-full hover:bg-gray-50" aria-label="Mark review as not helpful">
        <ThumbsDownIcon class="w-4 h-4 text-gray-600" />
      </button>
      <a href="#" class="text-sm text-gray-600 hover:underline">Report</a>
    </div>

  </div>
</template>

<script setup>
import { ThumbsUpIcon, ThumbsDownIcon } from 'lucide-vue-next'
</script>