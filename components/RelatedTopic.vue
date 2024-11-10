<template>
    <div class="max-w-3xl mx-auto space-y-8 m-5 ml-2">
      <!-- Topics Section -->
      <section>
        <h2 class="text-2xl font-semibold text-gray-900 mb-4 ">Explore related topics</h2>
        <div class="flex flex-wrap gap-3">
          <button
            v-for="topic in topics"
            :key="topic"
            @click="handleTopicClick(topic)"
            class="px-4 py-2 rounded-full border border-gray-300 hover:border-gray-400 
                   text-gray-700 hover:text-gray-900 transition-colors duration-200
                   text-sm whitespace-nowrap hover:bg-gray-100"
          >
            {{ topic }}
          </button>
        </div>
      </section>
  
      <!-- Companies Section -->
      <section class="border border-gray-200 rounded-lg p-6">
        <h3 class="text-lg font-semibold text-gray-900 mb-2">
          Top companies offer this course to their employees
        </h3>
        <p class="text-gray-600 text-sm mb-6">
          This course was selected for our collection of top-rated courses trusted by businesses worldwide.
          <a href="#" class="text-indigo-600 hover:text-indigo-800 font-medium">Learn more</a>
        </p>
  
        <div class="grid grid-cols-2 md:grid-cols-5 gap-8 items-center">
          <div v-for="(company, index) in companies" 
               :key="index" 
               class="flex items-center justify-center">
            <img 
              :src="company.logo" 
              :alt="`${company.name} logo`"
              class="max-h-8 w-auto object-contain company-logo"
            />
          </div>
        </div>
      </section>
    </div>
  </template>
  
  <script setup>
  const topics = [
    'Google Cloud Professional Data Engineer',
    'Google Cloud Professional Cloud Architect',
    'Software Testing',
    'Development'
  ]
  
  const companies = [
    {
      name: 'Nasdaq',
      logo: 'https://s.udemycdn.com/partner-logos/v4/nasdaq-dark.svg'
    },
    {
      name: 'Volkswagen',
      logo: 'https://s.udemycdn.com/partner-logos/v4/volkswagen-dark.svg'
    },
    {
      name: 'Box',
      logo: 'https://s.udemycdn.com/partner-logos/v4/box-dark.svg'
    },
    {
      name: 'NetApp',
      logo: 'https://s.udemycdn.com/partner-logos/v4/netapp-dark.svg'
    },
    {
      name: 'Eventbrite',
      logo: 'https://s.udemycdn.com/partner-logos/v4/eventbrite-dark.svg'
    }
  ]
  
  const handleTopicClick = (topic) => {
    console.log(`Selected topic: ${topic}`)
    // Add your navigation or filtering logic here
  }
  </script>
  
  <style scoped>
  .company-logo {
    filter: grayscale(1);
    transition: filter 0.2s ease-in-out;
  }
  
  .company-logo:hover {
    filter: grayscale(0);
  }
  </style>