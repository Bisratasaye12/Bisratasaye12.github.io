<template>
  <client-only>
    <div class="max-w-3xl mx-auto p-6 space-y-6 m-3 ml-3">
      <!-- Requirements Section -->
      <section>
        <h2 class="text-2xl font-bold text-gray-900 mb-4">Requirements</h2>
        <ul class="list-disc list-inside space-y-1">
          <li>
            <span class="text-gray-700">Basic </span>
            <span class="text-gray-600">understanding</span>
            <span class="text-gray-700"> of technology - </span>
            <span class="text-gray-600">superficial exposure to Hadoop is enough</span>
          </li>
        </ul>
      </section>
  
      <!-- Description Section -->
      <section>
        <h2 class="text-sm font-bold text-gray-900 mb-4">Description</h2>
        <div class="space-y-2">
          <p class="text-gray-700">
            This course is a really comprehensive guide to the 
            <span class="font-semibold">Google Cloud Platform - it has ~25 hours of content and ~60 demos.</span>
          </p>
          
          <p class="text-gray-700">
            The Google Cloud Platform is not currently the most popular cloud offering out there - that's AWS of course - but it is possibly the best cloud offering for high-end machine learning applications. That's because TensorFlow, the super-popular deep learning technology is also from Google.
          </p>
  
          <div class="space-y-3">
            <h3 class="font-bold text-gray-900">What's Included:</h3>
            <div class="relative">
              <ul class="space-y-3">
                <li v-for="(item, index) in items" 
                    :key="item.title"
                    class="flex gap-1">
                  <span class="font-bold text-gray-900">{{ item.title }}</span>
                  <span class="text-gray-700">-</span>
                  <span class="text-gray-600">{{ item.description }}</span>
                </li>
              </ul>
              <div v-if="isCollapsed" class="absolute bottom-0 left-0 right-0 h-24 bg-gradient-to-t from-white to-transparent"></div>
            </div>
          </div>
  
          <transition
            enter-active-class="transition duration-300 ease-out"
            enter-from-class="transform -translate-y-4 opacity-0"
            enter-to-class="transform translate-y-0 opacity-100"
            leave-active-class="transition duration-200 ease-in"
            leave-from-class="transform translate-y-0 opacity-100"
            leave-to-class="transform -translate-y-4 opacity-0"
          >
            <div v-if="!isCollapsed" class="space-y-4">
              <div class="space-y-3">
                <h3 class="font-bold text-gray-900">Who this course is for:</h3>
                <ul class="list-disc list-inside space-y-2 text-gray-600">
                  <li>Yep! Anyone looking to use the Google Cloud Platform in their organizations</li>
                  <li>Yep! Any one who is interesting in architecting compute, networking, loading balancing and other solutions using the GCP</li>
                  <li>Yep! Any one who wants to deploy serverless analytics and big data solutions on the Google Cloud</li>
                  <li>Yep! Anyone looking to build TensorFlow models and deploy them on the cloud</li>
                </ul>
              </div>
            </div>
          </transition>
  
          <button 
            @click="toggleCollapse"
            class="mt-4 text-blue-500 hover:text-blue font-semibold flex items-center gap-1"
          >
            {{ isCollapsed ? 'Show more' : 'Show less' }}
            <ChevronDownIcon 
              class="w-4 h-4 transition-transform duration-300"
              :class="{ 'transform rotate-180': !isCollapsed }"
            />
          </button>
        </div>
      </section>
    </div>
  </client-only>
</template>
  
<script setup>
import { ref, defineAsyncComponent } from 'vue'

// Dynamically import ChevronDownIcon to make it SSR-compatible
const ChevronDownIcon = defineAsyncComponent(() => import('lucide-vue-next').then(module => module.ChevronDownIcon))

const isCollapsed = ref(true)


const items = [
  {
    title: 'Compute and Storage',
    description: 'AppEngine, Container Enginer (aka Kubernetes) and Compute Engine'
  },
  {
    title: 'Big Data and Managed Hadoop',
    description: 'Dataproc, Dataflow, BigTable, BigQuery, Pub/Sub'
  },
  {
    title: 'TensorFlow',
    description: 'on the Cloud - what neural networks and deep learning really are, how neurons work and how neural networks are trained'
  },
  {
    title: 'DevOps stuff',
    description: 'StackDriver logging, monitoring, cloud deployment manager'
  },
  {
    title: 'Security',
    description: 'Identity and Access Management, Identity-Aware proxying, OAuth, API Keys, service accounts'
  },
  {
    title: 'Networking',
    description: 'Virtual Private Clouds, shared VPCs, Load balancing at the network, transport and HTTP layer; VPN, Cloud Interconnect and CDN Interconnect'
  },
  {
    title: 'Hadoop Foundations',
    description: 'A quick look at the open-source cousins (Hadoop, Spark, Pig, Hive and HBase)'
  }
]

const toggleCollapse = () => {
  isCollapsed.value = !isCollapsed.value
}
</script>
  
<style scoped>
.list-disc {
  list-style-type: disc;
}
</style>
