<!-- components/InfoCard.vue -->
<template>
    <div class="bg-white p-6 rounded-lg shadow-lg mb-6 animate__animated animate__fadeIn">
      <h2 class="text-2xl font-bold mb-2">{{ title }}</h2>
      <p class="text-gray-700">{{ description }}</p>
    </div>
  </template>
  
  <script>
  export default {
    name: 'InfoCard',
    props: {
      title: {
        type: String,
        required: true
      },
      description: {
        type: String,
        required: true
      }
    }
  }
  </script>
  