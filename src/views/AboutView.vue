<script setup>
import MainLayout from '@/components/MainLayout.vue';
import { reactive } from 'vue'

// Reactive array of students and a new student object
const students = reactive([
  { name: 'Amit', age: 15, class: '10th' },
  { name: 'Priya', age: 16, class: '11th' },
  { name: 'Rahul', age: 17, class: '12th' },
  { name: 'Neha', age: 14, class: '9th' },
  { name: 'Vikram', age: 16, class: '11th' }
])

// New student object for the form
const newStudent = reactive({
  name: '',
  age: '',
  class: ''
})

// Function to add a new student to the array
const addStudent = () => {
  if (newStudent.name && newStudent.age && newStudent.class) {
    students.push({ ...newStudent })
    newStudent.name = ''
    newStudent.age = ''
    newStudent.class = ''
  }
}
</script>

<template>
  <MainLayout>

    <div class="student-list p-6 bg-gray-100 min-h-screen">
      <h1 class="text-3xl font-bold text-center mb-8">Student List</h1>
  
      <!-- Form to add a new student -->
      <div class="max-w-lg mx-auto mb-8 p-6 bg-white shadow-md rounded-md">
        <h2 class="text-2xl font-semibold mb-4">Add New Student</h2>
        <form @submit.prevent="addStudent">
          <!-- Name input -->
          <div class="mb-4">
            <label for="name" class="block text-gray-700 mb-2">Name:</label>
            <input v-model="newStudent.name" type="text" id="name" class="w-full p-2 border border-gray-300 rounded-md focus:outline-none focus:ring focus:ring-blue-500" placeholder="Enter name" />
          </div>
          <!-- Age input -->
          <div class="mb-4">
            <label for="age" class="block text-gray-700 mb-2">Age:</label>
            <input v-model="newStudent.age" type="number" id="age" class="w-full p-2 border border-gray-300 rounded-md focus:outline-none focus:ring focus:ring-blue-500" placeholder="Enter age" />
          </div>
          <!-- Class input -->
          <div class="mb-4">
            <label for="class" class="block text-gray-700 mb-2">Class:</label>
            <input v-model="newStudent.class" type="text" id="class" class="w-full p-2 border border-gray-300 rounded-md focus:outline-none focus:ring focus:ring-blue-500" placeholder="Enter class" />
          </div>
          <!-- Submit button -->
          <button type="submit" class="w-full bg-blue-500 text-white py-2 px-4 rounded-md hover:bg-blue-600 focus:outline-none">Add Student</button>
        </form>
      </div>
  
      <!-- Student list display -->
      <ul class="space-y-6">
        <li v-for="(student, index) in students" :key="index" class="bg-white shadow-md p-4 rounded-md">
          <p class="text-xl font-semibold text-gray-800">Name: <span class="font-normal">{{ student.name }}</span></p>
          <p class="text-lg text-gray-600">Age: <span class="font-medium">{{ student.age }}</span></p>
          <p class="text-lg text-gray-600">Class: <span class="font-medium">{{ student.class }}</span></p>
        </li>
      </ul>
    </div>
  </MainLayout>
</template>

<style>
/* Add custom styles here if needed */
</style>
