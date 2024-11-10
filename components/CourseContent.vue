<template>
    <div class="max-w-3xl mx-auto border border-gray-200 rounded-lg m-3 ml-3">
      <!-- Header -->
      <div class="px-6 py-4 flex justify-between items-center">
        <h2 class="text-2xl font-semibold text-gray-900">Course content</h2>
        <div class="text-sm text-gray-600 space-x-4">
          <span>{{ courseSummary }}</span>
          <button 
            @click="toggleAllSections" 
            class="text-indigo-600 hover:text-indigo-800 font-medium"
          >
            {{ allExpanded ? 'Collapse' : 'Expand' }} all sections
          </button>
        </div>
      </div>
  
      <div class="divide-y divide-gray-200 bg-gray-100">
        <div v-for="section in sections" :key="section.id" class="divide-y ">
          <button 
            @click="toggleSection(section.id)"
            class="w-full px-6 py-4 flex justify-between items-center hover:bg-gray-50 transition-colors duration-150"
            :class="{ 'bg-gray-50': expandedSections[section.id] }"
          >
            <div class="flex items-center gap-3">
              <ChevronDownIcon 
                class="w-5 h-5 transition-transform duration-200"
                :class="[
                  expandedSections[section.id] ? 'text-gray-900' : 'text-gray-400',
                  { 'transform rotate-180': !expandedSections[section.id] }
                ]"
              />
              <span class="font-medium" :class="expandedSections[section.id] ? 'text-gray-900' : 'text-gray-700'">
                {{ section.title }}
              </span>
            </div>
            <span class="text-sm text-gray-500">
              {{ section.lectures }} lectures • {{ formatTime(section.duration) }}
            </span>
          </button>
  
          <!-- Section Content -->
          <div v-show="expandedSections[section.id]" class="bg-white">
            <div v-for="lecture in section.content" :key="lecture.id " 
                 class="px-6 py-3 flex items-center justify-between ">
              <div class="flex items-center gap-2">
                <component 
                  :is="getIcon(lecture.type)"
                  class="w-5 h-5 text-gray-400"
                />
                <span class="text-gray-600">{{ lecture.title }}</span>
              </div>
              <div class="flex items-center gap-4">
                <a v-if="lecture.preview"
                   href="#"
                   class="text-sm text-indigo-600 hover:text-indigo-800 font-medium"
                   @click.prevent="handlePreview(lecture)">
                  Preview
                </a>
                <span class="text-sm text-gray-500">{{ formatTime(lecture.duration) }}</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref, computed } from 'vue'
  import { ChevronDownIcon, PlayCircleIcon, FileTextIcon } from 'lucide-vue-next'
  
  const sections = [
    {
      id: 1,
      title: 'You, This Course and Us',
      lectures: 2,
      duration: 120, // in seconds
      content: [
        {
          id: 1,
          title: 'You, This Course and Us',
          type: 'video',
          duration: 121,
          preview: true
        },
        {
          id: 2,
          title: 'Course Materials',
          type: 'document',
          duration: 11,
          preview: true
        }
      ]
    },
    {
      id: 2,
      title: 'Introduction',
      lectures: 4,
      duration: 1440, // 24 minutes
      content: [
        {
          id: 3,
          title: 'Theory, Practice and Tests',
          type: 'video',
          duration: 626,
          preview: true
        },
        {
          id: 4,
          title: 'Lab: Setting Up A GCP Account',
          type: 'video',
          duration: 419,
          preview: true
        },
        {
          id: 5,
          title: 'Lab: Using The Cloud Shell',
          type: 'video',
          duration: 361,
          preview: false
        },
        {
          id: 6,
          title: 'Important! Delete unused GCP projects/instances',
          type: 'document',
          duration: 20,
          preview: false
        }
      ]
    },
    {
        id: 33,
        title: 'Compute',
        lectures: 14,
        duration: 5520, // 1hr 32min
        content: [
            { id: 1, title: 'About this section', type: 'document', duration: 15, preview: false },
            { id: 2, title: 'Compute Options', type: 'video', duration: 556, preview: false },
            { id: 3, title: 'Google Compute Engine (GCE)', type: 'video', duration: 458, preview: false },
            { id: 4, title: 'Lab: Creating a VM Instance', type: 'video', duration: 359, preview: true },
            { id: 5, title: 'More GCE', type: 'video', duration: 492, preview: false },
            { id: 6, title: 'Lab: Editing a VM Instance', type: 'video', duration: 285, preview: false },
            { id: 7, title: 'Lab: Creating a VM Instance Using The Command Line', type: 'video', duration: 283, preview: false },
            { id: 8, title: 'Lab: Creating And Attaching A Persistent Disk', type: 'video', duration: 240, preview: false },
            { id: 9, title: 'Google Container Engine - Kubernetes (GKE)', type: 'video', duration: 633, preview: false },
            { id: 10, title: 'More GKE', type: 'video', duration: 594, preview: false },
            { id: 11, title: 'Lab: Creating A Kubernetes Cluster And Deploying A Wordpress Container', type: 'video', duration: 415, preview: false },
            { id: 12, title: 'App Engine', type: 'video', duration: 408, preview: false },
            { id: 13, title: 'Contrasting App Engine, Compute Engine and Container Engine', type: 'video', duration: 362, preview: false },
            { id: 14, title: 'Lab: Deploy And Run An App Engine App', type: 'video', duration: 449, preview: false }
        ]
    },
    {
        id: 22,
        title: 'Storage',
        lectures: 15,
        duration: 5580, // 1hr 33min
        content: [
            { id: 1, title: 'About this section', type: 'document', duration: 11, preview: false },
            { id: 2, title: 'Storage Options', type: 'video', duration: 588, preview: false },
            { id: 3, title: 'Quick Take', type: 'video', duration: 821, preview: false },
            { id: 4, title: 'Cloud Storage', type: 'video', duration: 637, preview: false },
            { id: 5, title: 'Lab: Working With Cloud Storage Buckets', type: 'video', duration: 325, preview: false },
            { id: 6, title: 'Lab: Bucket And Object Permissions', type: 'video', duration: 232, preview: false },
            { id: 7, title: 'Lab: Life cycle Management On Buckets', type: 'video', duration: 306, preview: false },
            { id: 8, title: 'Fix for AccessDeniedException: 403 Insufficient Permission', type: 'document', duration: 30, preview: false },
            { id: 9, title: 'Lab: Running A Program On a VM Instance And Storing Results on Cloud Storage', type: 'video', duration: 429, preview: false },
            { id: 10, title: 'Transfer Service', type: 'video', duration: 306, preview: true },
            { id: 11, title: 'Lab: Migrating Data Using The Transfer Service', type: 'video', duration: 332, preview: false },
            { id: 12, title: 'gcloud init', type: 'video', duration: 5, preview: false },
            { id: 13, title: 'Lab: Cloud Storage ACLs and API access with Service Account', type: 'video', duration: 467, preview: false },
            { id: 14, title: 'Lab: Cloud Storage Customer-Supplied Encryption Keys and Life-Cycle Management', type: 'video', duration: 567, preview: false },
            { id: 15, title: 'Lab: Cloud Storage Versioning, Directory Sync', type: 'video', duration: 521, preview: false }
        ]
    },
    {
        id: 322,
        title: 'Cloud SQL, Cloud Spanner ~ OLTP ~ RDBMS',
        lectures: 9,
        duration: 3300, // 55min
        content: [
            { id: 1, title: 'About this section', type: 'document', duration: 15, preview: false },
            { id: 2, title: 'Cloud SQL', type: 'video', duration: 460, preview: false },
            { id: 3, title: 'Lab: Creating A Cloud SQL Instance', type: 'video', duration: 474, preview: false },
            { id: 4, title: 'Lab: Running Commands On Cloud SQL Instance', type: 'video', duration: 391, preview: false },
            { id: 5, title: 'Lab: Bulk Loading Data Into Cloud SQL Tables', type: 'video', duration: 549, preview: false },
            { id: 6, title: 'Cloud Spanner', type: 'video', duration: 445, preview: false },
            { id: 7, title: 'More Cloud Spanner', type: 'video', duration: 558, preview: false },
            { id: 8, title: 'Lab: Working With Cloud Spanner', type: 'video', duration: 409, preview: false },
            { id: 9, title: 'Important! Delete unused GCP projects/instances', type: 'document', duration: 21, preview: false }
        ]
    },
    {
        id: 3224,
        title: 'Hadoop Pre-reqs and Context',
        lectures: 1,
        duration: 60, // 1min
        content: [
            { id: 1, title: 'About this section', type: 'document', duration: 60, preview: false }
        ]
    }
  ]
  
  const expandedSections = ref({})
  const allExpanded = ref(false)
  
  // Initialize all sections as expanded
  sections.forEach(section => {
    expandedSections.value[section.id] = false
  })
  
  const courseSummary = computed(() => {
    const totalSections = sections.length
    const totalLectures = sections.reduce((acc, section) => acc + section.lectures, 0)
    const totalDuration = sections.reduce((acc, section) => acc + section.duration, 0)
    return `${totalSections} sections • ${totalLectures} lectures • ${formatTime(totalDuration)} total length`
  })
  
  const toggleSection = (sectionId) => {
    expandedSections.value[sectionId] = !expandedSections.value[sectionId]
    updateAllExpandedState()
  }
  
  const toggleAllSections = () => {
    const newState = !allExpanded.value
    sections.forEach(section => {
      expandedSections.value[section.id] = newState
    })
    allExpanded.value = newState
  }
  
  const updateAllExpandedState = () => {
    allExpanded.value = sections.every(section => expandedSections.value[section.id])
  }
  
  const formatTime = (seconds) => {
    if (seconds < 60) return `${seconds}s`
    const minutes = Math.floor(seconds / 60)
    const hours = Math.floor(minutes / 60)
    const remainingMinutes = minutes % 60
    
    if (hours > 0) {
      return `${hours}hr ${remainingMinutes}min`
    }
    return `${minutes}min`
  }
  
  const getIcon = (type) => {
    return type === 'video' ? PlayCircleIcon : FileTextIcon
  }
  
  const handlePreview = (lecture) => {
    console.log('Preview lecture:', lecture.title)
    // Implement preview functionality
  }
  </script>