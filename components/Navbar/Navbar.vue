<template>
  <header class="header border-b border-gray-200">
    <nav class="px-4 md:px-6 py-2.5 flex items-center justify-between gap-4">
      <div class="flex items-center gap-4">
        <Logo />
        <CategoriesButton />
      </div>

      <SearchBar :isIconActive="isIconActive" @update:iconActive="isIconActive = $event" />

      <div class="flex items-center gap-2 md:gap-4">
        <button class="sm:hidden">
          <Search class="h-5 w-5" />
        </button>

        <NavLinks />

        <button class="relative">
          <ShoppingCart class="h-5 w-5" />
          <span
            class="absolute -top-1 -right-1 h-4 w-4 text-xs flex items-center justify-center bg-purple-600 text-white rounded-full">
            1
          </span>
        </button>

        <AuthButtons />

        <MobileMenuButton />
      <button class="hidden md:flex items-center justify-center w-10 h-10 hover:bg-gray-100 rounded-0 border border-black">
     <Globe class="h-5 w-5" />
      </button>

      </div>
    </nav>

    <div class="p-4 sm:hidden">
      <SearchBar />
    </div>
  </header>
</template>

<script setup>
import Logo from './Logo.vue'
import CategoriesButton from './CategoriesButton.vue'
import SearchBar from './SearchBar.vue'
import NavLinks from './NavLinks.vue'
import AuthButtons from './AuthButtons.vue'
import MobileMenuButton from './MobileMenuButton.vue'
import { Search, ShoppingCart, Globe } from 'lucide-vue-next'
import { ref } from 'vue'



</script>
