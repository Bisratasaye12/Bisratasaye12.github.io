<template>
  <div class="relative">
    <button
      @mouseenter="showPopover"
      @mouseleave="hidePopoverDelayed"
      :class="[
        'hidden md:flex items-center text-sm font-medium transition-colors duration-200',
        hoverColor ? `hover:text-${hoverColor}` : 'hover:text-purple-600'
      ]"
    >
      {{ label }}
    </button>
    <transition
      enter-active-class="transition duration-200 ease-out"
      enter-from-class="transform scale-95 opacity-0"
      enter-to-class="transform scale-100 opacity-100"
      leave-active-class="transition duration-150 ease-in"
      leave-from-class="transform scale-100 opacity-100"
      leave-to-class="transform scale-95 opacity-0"
    >
      <div
        v-if="isPopoverVisible && popoverContent"
        @mouseenter="showPopover"
        @mouseleave="hidePopoverDelayed"
        class="absolute z-10 mt-2 w-80 rounded-md shadow-lg bg-white ring-1 ring-black ring-opacity-5"
      >
        <div class="p-4 space-y-4">
          <p class="text-sm font-medium text-center text-gray-700">
            {{ popoverContent }}
          </p>
          <button
            v-if="popoverButtonText"
            @click="$emit('popover-button-click')"
            :class="[
              'w-full px-4 py-2 text-sm font-medium text-white rounded-md transition-colors duration-200',
              popoverButtonColor
            ]"
          >
            {{ popoverButtonText }}
          </button>
        </div>
      </div>
    </transition>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const props = defineProps({
  label: {
    type: String,
    required: true
  },
  hoverColor: {
    type: String,
    default: 'purple-600'
  },
  popoverContent: {
    type: String,
    default: 'Get your team access to over 27,000 top Udemy courses, anytime, anywhere.'
  },
  popoverButtonText: {
    type: String,
    default: ' Try Udemy for Business'
  },
  popoverButtonColor: {
    type: String,
    default: 'bg-zinc-800 hover:bg-zinc-700'
  }
})

const emit = defineEmits(['popover-button-click'])

const isPopoverVisible = ref(false)
let hideTimeout = null

const showPopover = () => {
  clearTimeout(hideTimeout)
  isPopoverVisible.value = true
}

const hidePopoverDelayed = () => {
  hideTimeout = setTimeout(() => {
    isPopoverVisible.value = false
  }, 300)
}
</script>