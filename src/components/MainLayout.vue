<template>
    <div>
      <Header />
      <main>
        <slot></slot> <!-- This is where the page content will be injected -->
      </main>
      <Footer />
    </div>
  </template>
  
  <script setup>
  import Header from './Header.vue'
  import Footer from './Footer.vue'
  </script>
  
  <style scoped>
  /* Add any specific styles here */
  </style>
  