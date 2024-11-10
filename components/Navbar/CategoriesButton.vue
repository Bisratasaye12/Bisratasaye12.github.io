<template>
  <div class="relative">
    <button 
      @mouseenter="showDropdown = true"
      class="flex items-center space-x-2 px-4 py-2 hover:text-purple-600 transition-colors duration-200"
    >
      <span>Categories</span>
    </button>

    <div 
      v-if="showDropdown"
      @mouseleave="hideDropdown"
      class="absolute top-full left-0 w-[480px] bg-white shadow-lg rounded-md z-50 overflow-hidden"
    >
      <div class="flex">
        <div class="w-1/2 bg-gray-50 py-2">
          <div 
            v-for="category in categories" 
            :key="category.name" 
            @mouseenter="activeCategory = category"
            class="px-4 py-2 hover:bg-white cursor-pointer transition-colors duration-200"
            :class="{ 'bg-white': activeCategory === category }"
          >
            <div class="flex items-center justify-between">
              <span class="text-sm text-gray-700">{{ category.name }}</span>
              <ChevronRightIcon class="w-4 h-4 text-gray-400" />
            </div>
          </div>
        </div>
        
        <div v-if="activeCategory" class="w-1/2 bg-white py-2">
          <div 
            v-for="subCategory in activeCategory.subCategories" 
            :key="subCategory"
            class="px-4 py-2 hover:bg-gray-100 cursor-pointer transition-colors duration-200"
          >
            <span class="text-sm text-gray-700">{{ subCategory }}</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { ChevronDownIcon, ChevronUpIcon, ChevronRightIcon } from 'lucide-vue-next'

const showDropdown = ref(false)
const activeCategory = ref(null)
const categories = [
  { 
    name: 'Development',
    subCategories: ['Web Development', 'Mobile Development', 'Game Development', 'Database Design']
  },
  { 
    name: 'Business',
    subCategories: ['Entrepreneurship', 'Communication', 'Management', 'Sales']
  },
  { 
    name: 'Finance & Accounting',
    subCategories: ['Accounting', 'Cryptocurrency', 'Economics', 'Investing']
  },
  { 
    name: 'IT & Software',
    subCategories: ['IT Certifications', 'Network Security', 'Hardware', 'Operating Systems']
  },
  { 
    name: 'Office Productivity',
    subCategories: ['Microsoft Office', 'Google Workspace', 'SAP', 'Apple Productivity Tools']
  },
  { 
    name: 'Personal Development',
    subCategories: ['Personal Transformation', 'Productivity', 'Leadership', 'Career Development']
  },
  { 
    name: 'Design',
    subCategories: ['Graphic Design', 'Web Design', '3D & Animation', 'User Experience']
  },
  { 
    name: 'Marketing',
    subCategories: ['Digital Marketing', 'Content Marketing', 'Branding', 'Social Media Marketing']
  },
  { 
    name: 'Lifestyle',
    subCategories: ['Arts & Crafts', 'Gaming', 'Travel', 'Beauty & Makeup']
  },
  { 
    name: 'Photography & Video',
    subCategories: ['Digital Photography', 'Video Production', 'Video Editing', 'Photography Fundamentals']
  },
  { 
    name: 'Health & Fitness',
    subCategories: ['Fitness', 'Mental Health', 'Yoga', 'Nutrition']
  },
  { 
    name: 'Music',
    subCategories: ['Music Production', 'Instrument Lessons', 'Music Theory', 'Vocal Training']
  },
  { 
    name: 'Teaching & Academics',
    subCategories: ['Online Education', 'Academic Writing', 'Test Prep', 'Language Learning']
  }
];


const hideDropdown = () => {
  showDropdown.value = false
  activeCategory.value = null
}
</script>

<style scoped>
.group {
  position: relative;
}
</style>