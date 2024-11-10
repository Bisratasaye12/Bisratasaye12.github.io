<template>
    <div class="flex-1 max-w-3xl relative hidden sm:block">
        <div class="relative">
            <input name="searchField" type="search" placeholder="Search for anything"
                class="search-input w-full py-2.5 pl-12 pr-4 border border-gray-300 rounded-full bg-gray-50 focus:bg-white focus:outline-none text-sm"
                @focus-within="isIconActive(true)" @blur="isIconActive(false)" />
            <Search class="absolute left-4 top-1/2 -translate-y-1/2 h-5 w-5" :class="{ 'icon-active': iconActive }" />
        </div>
    </div>
</template>

<script setup>
import { ref } from 'vue'
import { Search } from 'lucide-vue-next'

const iconActive = ref(false)

// Function to toggle iconActive based on focus status
function isIconActive(active) {
    iconActive.value = active
}
</script>

<style scoped>
/* Optional: Remove purple outline on focus */
.search-input:focus {
    outline: none;
    box-shadow: none;
}

/* Icon color when input is focused */
.icon-active {
    color: blue
}
</style>
