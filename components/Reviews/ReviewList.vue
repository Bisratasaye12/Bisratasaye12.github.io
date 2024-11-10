<!-- ReviewList.vue -->
<template>
    <div>
        <div class="grid md:grid-cols-2 gap-6">
      <ReviewItem 
        v-for="review in displayedReviews" 
        :key="review.id"
        :review="review"
        :onHelpful="handleHelpful(review.id)"
      />
    </div>
  
    <div class="mt-8 text-center" v-if="hasMoreReviews">
      <button 
        @click="showMore"
        class="px-6 py-2 border rounded-lg hover:bg-gray-50 transition-colors"
      >
        Show all reviews
      </button>
    </div>
    </div>
  </template>
  
  <script setup>
  import { ref, computed } from 'vue'
  import ReviewItem from './ReviewItem.vue'
  
  const rating = '3.1'
  const totalRatings = '7K'
  const itemsPerPage = 4
  
  const reviews = ref([
    {
      id: 1,
      name: 'Dilip K.',
      initials: 'DK',
      rating: 3,
      timeAgo: '2 months ago',
      content: 'It is very mechanical ....it should talk about reference to business the use case',
      userVote: null
    },
    {
    id: 2,
    name: 'Vijayakumar A.',
    initials: 'VA',
    rating: 4,
    timeAgo: '8 months ago',
    content: 'Good',
    userVote: null
  },
  {
    id: 3,
    name: 'Godhuli P.',
    initials: 'GP',
    rating: 5,
    timeAgo: '11 months ago',
    content: 'informative',
    userVote: null
  },
  {
    id: 4,
    name: 'Sukanta D.',
    initials: 'SD',
    rating: 5,
    timeAgo: '11 months ago',
    content: 'sdfvbn',
    userVote: null
  },
  {
    id: 5,
    name: 'John D.',
    initials: 'JD',
    rating: 4,
    timeAgo: '1 year ago',
    content: 'Very helpful course with practical examples',
    userVote: null
  },
  {
    id: 6,
    name: 'Sarah M.',
    initials: 'SM',
    rating: 5,
    timeAgo: '1 year ago',
    content: 'Excellent content and well explained',
    userVote: null
  }
  ])
  
  const visibleItems = ref(itemsPerPage)
  
  const displayedReviews = computed(() => {
    return reviews.value.slice(0, visibleItems.value)
  })
  
  const hasMoreReviews = computed(() => {
    return visibleItems.value < reviews.value.length
  })
  
  const showMore = () => {
    visibleItems.value = reviews.value.length
  }
  
  const handleHelpful = (reviewId, isHelpful) => {
    const review = reviews.value.find(r => r.id === reviewId)
    if (review) {
      review.userVote = review.userVote === (isHelpful ? 'up' : 'down') 
        ? null 
        : (isHelpful ? 'up' : 'down')
    }
  }
  </script>
  