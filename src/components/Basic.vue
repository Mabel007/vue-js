<template>
  <div class="main-container">
    <div class="p-5">
      <button class="bg-green-500 text-white px-4 py-2 rounded-lg hover:bg-blue-600" @click="increment">
    +
  </button>
  <span>The count is : {{ count}}</span>
  <button class="bg-blue-500 text-white px-4 py-2 rounded-lg hover:bg-blue-600" @click="decrement">
    -
  </button>
    </div>
  <h1>{{ message + 'AltSchool' }}</h1>
  <h3>{{ message.toUpperCase() }}</h3>
  <h2>{{ message.repeat(3) }}</h2>
  <h2>{{ message + 'AltSchool'.toUpperCase() }}</h2>
  <div>Current time: {{ formatDate(new Date()) }}</div>
  </div>

</template>

<script setup>

import { ref } from 'vue';
const count = ref(0);

function increment(){
  count.value++
}

function decrement(){
  count.value--
}

function formatDate(date){
  return date.toISOString();
}

const message = 'Hello, Vue 3!';
</script>