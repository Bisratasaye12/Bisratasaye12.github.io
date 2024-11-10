<template>
  <div class="max-w-2xl mx-auto p-6 m-3 ml-3">
    <div class="border rounded-lg p-6">
      <h2 class="text-xl font-bold text-gray-900 mb-4">Featured review</h2>
      <div>
        <UserAvatar name="Joy B." avatarSrc="/placeholder.svg?height=48&width=48" courses="1032 courses"
          reviews="37 reviews" class="mb-4" />

        <div class="flex-1">
          <Rating stars="4.5" time="5 years ago" />

          <p class="text-gray-700 mb-4">
            This Course is really Great.. This gives a meticulous focus on the topics with a sincere attitude.. The only
            reason I am putting 4.5 (not 5) is that I am not sure if this course is being updated per the Real Exam
            updates as of 2019.
          </p>

          <ReviewActions />
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import UserAvatar from './UserAvatar.vue'
import Rating from './Rating.vue'
import ReviewActions from './ReviewActions.vue'
</script>